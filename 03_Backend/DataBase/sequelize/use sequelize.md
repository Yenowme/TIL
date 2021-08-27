### 정의

ORM(Object-Relational Mapping) 관계형 데이터베이스의 데이터를 객체지향 패러다임을 활용하여 조작하는 기술. 쿼리를 직접 작성하지 않아도 객체의 메서드를 활용하는 것처럼 사용이 가능하다.

### 특징

- Promise 객체를 리턴하기 때문에 비동기 로직을 구현하기 수월하다.

---

## 사용

### 1. 초기화

`sequelize init`

- 생성 폴더
    - `config`: 데이터베이스 설정파일, 사용자이름, db이름 등 정보가 들어감

        → `env파일`을 활용해서 관리하는게 보안상 안전하다.

    - `migrations`: db의 up과 down의 히스토리를 관리한다.
        - `up`: 실제 db에 적용되는 부분
        - `down` : 작업 취소
    - `models`: db의 테이블정보 및 필드타입을 정의하고, 하나의 객체로 생성한다? 모은다?
    - `seeders`: 테이블에 기본 데이터를 넣고 싶을 때 사용
- 설정

    `config/config.json` 파일에 사용할 데이터베이스 관련 정보를 기입

    - ex

        ```json
        "development": {
          "username": "root",
          "password": "root",
          "database": "instagram",
          "host": "127.0.0.1",
          "dialect": "mysql",
          "operatorsAliases": false
        }
        ```

    - **`env` 파일로 변수 관리하기**
        - 방법
            1. config.json → config.js으로 수정
            2. 파일 재작성
                - ex

                    ```json
                    require("dotenv").config();
                    const env = process.env;

                    const development = {
                        username: env.MYSQL_USER,
                        password: env.MYSQL_PASSWORD,
                        database: env.MYSQL_DATABASE,
                        host: "127.0.0.1",
                        dialect: "mysql", //사용하는 db
                        port: env.MYSQL_PORT,
                    };
                    const test = {
                        username: "root",
                        password: null,
                        database: "database_test",
                        host: "127.0.0.1",
                        dialect: "mysql",
                    };
                    const production = {
                        username: "root",
                        password: null,
                        database: "database_production",
                        host: "127.0.0.1",
                        dialect: "mysql",
                    };

                    module.exports = { development, test, production };
                    ```

            3. model/index.js 수정

                config파일을 불러오는곳 수정

                `const config = require(__dirname + "/../config/config.js")[env];`

### 2. database 설정

- 모델 생성

    `sequelize model:generate`

    - cli

        `--name User`

        모델의 이름 생성

        `--attributes user_id:integer,user_name:string`

        하위 데이터타입 생성

    - 모델.js 에서 추가설정
        - sequelize model 생성시 sequelize 는 고유 키값을 정의해 주지 않아도, 다른 설정이 없다면 id 로 생성해주며 row 생성시 자동으로 1씩 증가한다.
        - id 이외에 createdAt(생성일), updatedAt(수정일) 도 같이 생성해준다.
        - `defaultValue`: row가 생성될때 기본값을 설정해줄 수 있다. (etc. Sequelize.NOW)
        - `allowNull`: false로 설정해주면 빈값으로 생성시 에러가 난다.(default true)
        - `unique`: 테이블내의 고유한 값(boolean)
        - `primaryKey`: 고유 키값 설정 여부
        - `autoIncrement`: 자동으로 값을 증가시켜준다. (Integer 에서만 사용 가능)
        - `field`: 객체 키값과 다르게 custom으로 컬럼명을 사용할 수 있게해준다.
        - `comment`: 해당 컬럼에 대한 설명을 달 수 있다. 컬럼 생성에 영향을 미치지는 않는다. 주석같은 개념
        - getter, setter

            [https://ko.javascript.info/property-accessors](https://ko.javascript.info/property-accessors)

    - 관계성 설정
- db 반영

    `sequelize db:migrate`

### 3. data 조정

모델이 만들어졌으면, 이제 코드 내에서 데이터를 조절할 차례이다.

1. 모듈 가져오기

    ```jsx
    const { sequlize, User } = require("../models");
    ```

    - `modules/index.js` 를 불러온다. `index.js`가 사용중인 다른 모델도 리턴하기 때문에 모델에서 한번에 `User`를 가져올 수 있다.
2. raw생성하기

    ```jsx
    router.post("/", async function (req, res, next) {
        const { username, email, isCardet, careerYears } = req.body;
        try {
            const user = await User.create({
                username,
                email,
                isCardet,
                careerYears,
            });

            return res.status(200).json(user);
        } catch (error) {
            console.log(error);
            return res.status(500).json(error);
        }
    });
    ```

    - post형식으로 값을 받아 리턴하는 예제이다. 해당 모델의 인스턴스로 create()를 사용하여 값을 넣어주면 된다
3. 모델 싱크 조정

    ```jsx
    sequelize db:migrate:undo:all
    sequelize db:migrate
    ```

    - db모델이 바뀌었으면 db테이블을 리셋해야한다. undo했다가 do하면 됨
    - 모델 말고 migration 파일도 변경해야함
    - 아니면 `sequelize.sync()` 를 코드에 넣어준다.
    - 모델은 코드가 가져올 때 중요함
    - 마이그레이션은 undo - do 할떄 중요함
4. 관계설정

    ```jsx
    //model>index.js
    const { text, user } = sequelize.models;
    text.belongsTo(user);
    user.hasMany(text);
    ```

    상호 설정 해주고 db undo-do 해주면 된다~

    [https://velog.io/@bigbrothershin/Backend-sequelize-MN-관계](https://velog.io/@bigbrothershin/Backend-sequelize-MN-%EA%B4%80%EA%B3%84)

    - find 해서 가져올 땐 include 로 가져온다.

### 정의

ORM(Object-Relational Mapping) 관계형 데이터베이스의 데이터를 객체지향 패러다임을 활용하여 조작하는 기술. 쿼리를 직접 작성하지 않아도 객체의 메서드를 활용하는 것처럼 사용이 가능하다.

### 특징

- Promise 객체를 리턴하기 때문에 비동기 로직을 구현하기 수월하다.
