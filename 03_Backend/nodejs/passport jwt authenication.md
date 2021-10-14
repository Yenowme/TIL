### 사용 모듈

- `cookie-parser` : 쿠키 헤더를 파싱해서 `req.cookies`객체에 저장
- `res.cookie(name, value,flag)` : 응답 헤더에 쿠키를 설정

    ```jsx
    res.cookie('imcookie', '1', {
    	expires: new Date(Date.now()+10000),
    	httpOnly:true
    })
    ```

    - value는 문자열 or JSON
    - expires: 쿠키 보증기간
    - httpOnly: 웹서버에서만 쿠키 사용
    - [기타 플래그](https://expressjs.com/ko/api.html)
- `jsonwebtoken` : jwt 생성, 검증 모듈
- `passport`
    - 인증 메커니즘을 모듈로 패키지화 해 제공
- `passport-jwt`
    - jwt를 사용한 passport인증
- `passport-local`
    - 아이디, 비밀번호 등 직접 구현할 때 사용

## 쿠키-JWT 로 유효성 검사

1. **jwt생성**

    ```jsx
    const jwt = require("jsonwebtoken");
    ~~~~jwt.sign(payload, secret, options, [callback])
    ```

    - 콜백함수의 파라미터는 `(err, token)`
    - 전달되지 않을시엔 동기적으로 작동하며, JWT 를 문자열 형태로 리턴.
    - `payload` 는  객체, buffer, 혹은 문자열
    - `secret` 은 서명을 만들 때 사용되는 알고리즘에서 사용되는 문자열 혹은 buffer 형태의 값
    - `options`
        - `algorithm`: 기본값은 `HS256` 으로 지정됩니다.
        - `expiresIn`: JWT 의 등록된 클레임중 `exp` 값을 x 초후 혹은 [rauchg/ms](https://github.com/rauchg/ms.js) 형태의 기간 후로 설정합니다.(예제: (60, “2 days”, “10h”, “7d”)
        - `notbefore`: `JWT` 의 등록된 클레임중 `nbf` 값을 x 초후 혹은 [rauchg/ms](https://github.com/rauchg/ms.js) 형태의 기간 후로 설정합니다.(예제: (60, “2 days”, “10h”, “7d”)
        - `audience`
        - `issuer`
        - `jwtid`
        - `subject`
        - `noTimestamp`
        - `header`
    - [https://jwt.io/](https://jwt.io/)  에서 복호화 해보기 가능
2. **res.cookie에 jwt 저장**

    ```jsx
    try {
            const token = jwt.sign(
                {
                    username: req.body.username,
                },
                secret,
                {
                    expiresIn: 120,
                }
            );
            console.log(token);
            res.cookie("token", token, {
                httpOnly: true,
                maxAge: 120000,
            });
            res.status(200).json({ msg: "🍪 여권 발급 성공! 🍪" });
        } catch (error) {
            console.log(error);
            next(["jwt make error"]);
    ```

3. jwt 검증

    ```jsx
    function validJWT(req, res, next) {
        const { token } = req.cookies;
        if (token) {
            try {
                jwt.verify(token, secret);
                next();
            } catch (error) {
                next(error);
            }
        } else {
            res.status(401).json({
                msg: "🍪 쿠키의 세상에 아무나 출입 할 수 없습니다!! 🍪",
                reason: ["token 검증 실패"],
            });
        }
    }
    ```

## passport-jwt 설정

1. **passport 설정**

    ```jsx
    //passprot/index.js

    var JwtStrategy = require('passport-jwt').Strategy,
        ExtractJwt = require('passport-jwt').ExtractJwt;

    var opts = {}
    opts.jwtFromRequest = ExtractJwt.fromAuthHeaderAsBearerToken();
    opts.secretOrKey = 'secret';
    //위는 필수
    opts.issuer = 'accounts.examplesoft.com';
    opts.audience = 'yoursite.net';
    //옵션설정

    module.exports= ()=>{ passport.use("jwt",new JwtStrategy(opts, function(jwt_payload, done) {
        User.findOne({id: jwt_payload.sub}, function(err, user) {
            if (err) {
                return done(err, false);
            }
            if (user) {
                return done(null, user);
            } else {
                return done(null, false);
                // or you could create a new account
            }
        });
    })); }
    ```

    - `new JwtStrategey(options, verify)`
        - `options`는 토큰을에대한 정보를 객체로 받는다.
            - `secretOrKey`
                - 토큰 사인을 인증할 시크릿키
            - 위에거 안쓰면 `secretOrKeyProvider`
                - `req`, `rawJwtToken`, `done` 을 매개변수로 받는 콜백함수
            - `jwtFromRequest`
                - 콜백함수로, 어디서 토큰을 뽑아올지에 대한 정보
                - 종류

                     `ExtractJwt.` 내장 메소드들 사용

                    - `fromAuthHeaderAsBearerToken()`
                        - req헤드로부터 토큰을 뽑아온다.
                    - `fromHeader(header_name)`
                    - `fromBodyField(field_name)`
                    - `fromUrlQueryParameter(param_name)`
                    - `fromAuthHeaderWithScheme(auth_scheme)`
                    - `fromAuthHeaderAsBearerToken()`
                    - `fromExtractors([array of extractor functions])`
                    - 직접 커스텀해서 사용 가능
                        - req에서 token을 리턴해오면 됨
        - `verify` 는 콜백함수로, 인증을 완료하면 실행된다.
            - 인자로 해석된 `payload`, 와 `done`을 받는다.
            - done은 매개변수로 `err` 와 `정보`를 받는다.
            - done으로 넘겨준 정보는 같은 첫번째 매개변수string을 가진 authenticate의 콜백함수로 넘어간다!
2. **passport 사용 설정**

    ```jsx
    //app.js

    const passport = require("passport");
    const passportConfig = require("./passport");
    ...
    app.use(passport.initialize());
    passportConfig();
    ...
    ```

    - `initialize()`로 사용 선언
    - `passportConfig();` 로 설정 불러와서 셋팅
3. 컨트롤러에서 사용

    ```jsx
    //controller/user.js
    const passport = require("passport");

    router.get("/", authPassport, passRes);

    function authPassport(req, res, next) {
        passport.authenticate("jwt", function (err, user) {
            if (err) {
                return res.status(500).json({
                    msg: "🍪 쿠키의 세상에 아무나 출입 할 수 없습니다!! 🍪",
                    reason: ["token authenticate err"],
                }); // will generate a 500 error
            }
            // Generate a JSON response reflecting authentication status
            if (!user) {
                return res.status(400).json({
                    msg: "🍪 쿠키의 세상에 아무나 출입 할 수 없습니다!! 🍪",
                    reason: ["token not valid"],
                });
            }
            console.log(info);
            req.user = user;
            next();
        })(req, res, next);
    }
    ```

    - `passport.authenticate` 를 미들웨어로 연결한 뒤 인증이 성공하면, 자동으로 next를 호출해 인증이 완료된다.
    - 아니면 위와같이 직접 콜백함수를 만들어 사용할 수도 있다. `authenticate`의 리턴이 아마 함수이기때문에 마지막에  `req,res,next`매개변수를 붙여준다.

### 참고

- [passport.js 공식 사이트](http://www.passportjs.org/)
    - [passport-jwt 공식 문서](http://www.passportjs.org/packages/passport-jwt/)
- [사용 정리 블로그](https://velog.io/@rolled-potatoes/node-passport-jwt)
