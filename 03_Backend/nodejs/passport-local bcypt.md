## passport-local

1. **app.js 셋팅**

    ```jsx
    // app.js
    const passport = require("passport");
    ...
    app.use(passport.initialize());
    ...
    ```

2. **passport/index.js 설정**

    여기서 passportConfig()를 실행하기 위한 설정을 지정해서 passport 인스턴스를 만들어준다.

    ```jsx
    //passport/index.js
    const passport = require("passport");
    const bcrypt = require("bcrypt");
    const LocalStrategy = require("passport-local").Strategy;

    const localStrategyOpt = {
        usernameField: "email",
        passwordField: "password",
    };
    //인증할 verify의 매개변수를 변경할 수 있다.

    async function localVerify(email, password, done) {
        let user;
        try {
            user = await Users.findOne({ where: { email } });
            if (!user) return done(null, false);
            const isSamePassword = await bcrypt.compare(password, user.password);
            if (!isSamePassword) return done(null, false);
        } catch (error) {
            done(error);
        }
        return done(null, user);
    }

    ```

    - `LocalStrategyOpt` : new LocalStrategy 의 첫번쨰 변수로, 이메일과 비밀번호를 입력값에서 추출해서 가져오도록 변경할 수 있다. (폼의 데이터 이름과 짝 맞추면 됨)
    - `localVerify` : 이메일과 비밀번호를 인증하는 방법에 대한 콜백함수를 정의할 수 있음.

3. **설정값을 다시 app.js에 셋팅**

    ```jsx
    // app.js
    const passport = require("passport");
    const passportConfig = require("./passport") //위에서 내보낸 설정 익명함수
    ...
    app.use(passport.initialize());
    passportConfig();
    ...
    ```

4. **인증 미들웨어로 활용**

    ```jsx
    const passport = require("passport");
    const jwt = require("jsonwebtoken");
    require("dotenv").config();
    const secret = process.env.JWT_SECRET_KEY;

    function createJwt(req, res, next) {
        passport.authenticate("local", { session: false }, (err, user) => {
            if (err) next(err);
            else if (!user) res.status(400).json({ msg: "유효하지 않은 값" });
            req.login(user, { session: false }, (err) => {
                if (err) next(err);
                const token = jwt.sign(
                    {
                        username: user.username,
                        email: user.email,
                    },
                    secret,
                    {
                        expiresIn: "2m",
                    }
                );
                return res.status(200).json({
                    msg: "login success",
                    token,
                });
            });
        })(req, res, next);
    }

    module.exports = { createJwt };
    ```

    req.login은 뜬금없는것 같지만, `passport.authenicate()` 가 자동으로 넣어주는 함수이다.

### 참고

- [전체 과정 정리 블로그](https://velog.io/@jakeseo_me/%EB%B2%88%EC%97%AD-passport-local%EC%97%90-%EB%8C%80%ED%95%B4-%EC%95%8C%EC%95%84%EC%95%BC-%ED%95%98%EB%8A%94-%EB%AA%A8%EB%93%A0-%EA%B2%83)
