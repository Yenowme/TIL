# validator
post 입력값이 유효한지 체크해주는 모듈
<br>
<br>
### 사용

1. **설치**

    ```jsx
    npm i validator
    ```
<br>

2. **불러오기**

    ```jsx
    import {check, validationResult} from "express-validator"
    ```
<br>

3. **간단한 사용**

    ```jsx
    router.post(
        "/",
        [
            check("name", "Name is required").not().isEmpty(),
            check("email", "Please include a valid email").isEmail()
        ]
        async (req, res) => {
            const errors = validationResult(req);
          // ...
        }
      );
    ```

    - check 첫번째 인자로 post의 key를, 두번째 인자로 오류 메세지를 받는다.
    - validationResult(req) 는 check를 통과하지 못한 에러들을 반환한다. 반환값이 비었다면 통과한것.
<br>
<br>

4. 미들웨어로 사용 //수정필요

    ```jsx
    async function validPost(req, res, next) {
        const { password, email, username } = req.body;
        if (!password || !email || !username)
            return res.status(400).json({
                msg: "값을 모두 입력해주세요.",
            });
        await check("password", "비밀번호는 8글자 이상, 대소문자 포함, 숫자 포함.")
            .matches(
                /^(?=.*[0-9])(?=.*[a-z])(?=.*[A-Z])(?=.*[*.!@$%^&\(\)\{\}\[\]:;<>,.?/~_+-=|]).{8,}$/,
                "i"
            )
            .notEmpty();
        await check("email", "유효하지 않은 이메일").isEmail().notEmpty().bail();
        await check("username", "유효하지 않은 username")
            .notEmpty()
            .matches(/^(?=.*\d)(?=.*[a-z]).{8,}$/)
            .bail();
        const err = validationResult(req);
        if (err) {
            console.log(err);
            res.status(400).json(err);
        } else next();
    }
    ```
<br>
<br>

- 옵션들
    - `trim()` : 공백을 제거해줍니다.
    - `isLength(num)` : 길이가 num인지 확인해줍니다. `{ min: num, max: num }` 과 같이 최소, 최대 값도 지정할 수 있습니다.
    - `bail()` : 해당 부분에서 에러가 발생하면 다음으로 넘어가지 않습니다.
    - `isNumeric()` : 숫자 형태이지 확인한다. string이어도 해당 string이 숫자인지 확인해줍니다.
    - `isEmail()` : string이 이메일 형태인지 확인해줍니다.
    - `isJSON()` : string이 유효한 JSON인지 확인해줍니다. JSON.parse를 사용한다고 합니다.
    - `isMobilePhone()` : string이 모바일 휴대폰 번호인지 확인해줍니다.
	- `matches(/regex/)` : 정규표현식 체크.

- [공식깃헙](https://github.com/validatorjs/validator.js)
