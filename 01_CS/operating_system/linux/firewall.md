# 방화벽

## UFW

-   `우분투`의 기본적인 방화벽. `iptables`를 쉽게 설정할 수 있도록 한 것이기 때문에 고급 설정은 `iptables` 를 직접 사용해야한다.

## 사용법

-   **설치**
    -   sudo apt install ufw
-   **활성화&비활성화**
    -   `sudo ufw enable`
    -   `sudo ufw disable`
-   **상태 확인**
    `sudo ufw status verbose`
-   **기본 룰**
    -   `UFW`는 기본 룰이 설정되어있음
        -   들어오는 패킷은 전부 거부
        -   나가는 패킷 전부 허가
    -   기본 룰 확인
        -   `sudo ufw show raw`
    -   기본 룰 허용&거부
        -   `sudo ufw default allow`
        -   `sudo ufw default deny`
-   **UFW 허용과 차단**
    -   `sudo ufw allow(or deny) <port>/<optional: protocal>(or service name)`
-   **UFW 룰 (서비스명) 확인**
    -   `less /etc/services`

## 참고

-   [UFW 공식 문서](https://help.ubuntu.com/community/UFW)
-   [설명 블로그](https://webdir.tistory.com/206)
