# arm_compile

직접 계정 입력하여 가져오기!! 

git remote add origin github-qfe051:qfe051/arm_compile.git

git fetch

git pull origin main

# 🛠️ arm_compile

ARM 기반 프로젝트를 위한 컴파일 예제 및 환경 설정 가이드입니다.  
개발자가 직접 계정을 입력하고 설정할 수 있도록 SSH 기반으로 remote를 연결합니다.

---

## 📦 프로젝트 구성

- `main.c` / `utils.c` : 간단한 ARM C 예제 코드
- `Makefile` : 컴파일 빌드 자동화
- `README.md` : 설정 및 실행 방법 안내

---

## 🔗 GitHub 원격 저장소 연결 방법

이 프로젝트는 퍼블릭 레포가 아니므로,  
**본인 계정으로 Fork 또는 클론 후 연결해야 합니다.**

### SSH 방식 (직접 계정 입력)

```bash
git remote add origin github-<your-alias>:<your-id>/arm_compile.git
git fetch
git pull origin main
```

예시:

```bash
git remote add origin github-qfe051:qfe051/arm_compile.git
git fetch
git pull origin main
```

> 📌 위의 `github-qfe051`은 `~/.ssh/config`에 설정된 Host 이름입니다.

---

## ⚙️ 사용법

1. 소스 수정
2. 컴파일
    ```bash
    make
    ```
3. 실행
    ```bash
    ./main
    ```

---

## 📁 참고

- SSH 설정 예시:
    ```ssh
    Host github-qfe051
      HostName github.com
      User git
      IdentityFile ~/.ssh/id_rsa_qfe051
    ```

---

## 🧑‍💻 작성자

- GitHub: [qfe051](https://github.com/qfe051)
