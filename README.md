<div align="center">

# 📸 Saragram (사라그램)
### Instagram-inspired SNS Project with Full-Stack Implementation

<img src="https://img.shields.io/badge/react-61DAFB?style=for-the-badge&logo=react&logoColor=black">
<img src="https://img.shields.io/badge/vite-646CFF?style=for-the-badge&logo=vite&logoColor=white">
<img src="https://img.shields.io/badge/node.js-339933?style=for-the-badge&logo=Node.js&logoColor=white">
<img src="https://img.shields.io/badge/express-000000?style=for-the-badge&logo=express&logoColor=white">
<img src="https://img.shields.io/badge/mysql-4479A1?style=for-the-badge&logo=mysql&logoColor=white">
<img src="https://img.shields.io/badge/sequelize-52B0E7?style=for-the-badge&logo=sequelize&logoColor=white">

<br/>

**인스타그램의 핵심 기능을 직접 구현하며 학습한 풀스택 프로젝트입니다.** RESTful API 설계부터 인증, 데이터베이스 모델링, 파일 업로드까지  
실무에서 사용되는 핵심 패턴을 깊이 있게 연구했습니다.

[👉 Live Demo (배포 링크가 있다면 입력)](https://your-deploy-url.com) | [📝 Blog Review (회고 글 링크)](https://your-blog-url.com)

</div>

<br/>

## 🧐 About Project
단순한 클론 코딩을 넘어, **"데이터는 어떻게 흐르고, 안전하게 관리되는가?"**에 집중했습니다.
프론트엔드와 백엔드를 모두 구축하며 유저, 게시글, 댓글 간의 **관계형 데이터 모델링(RDB)**을 이해하고, **JWT 기반의 인증 보안** 로직을 직접 구현하여 웹 서비스의 전체적인 아키텍처를 익혔습니다.

<br/>

## 🛠 Tech Stack

| 구분 | 기술 스택 |
| :--- | :--- |
| **Frontend** | ![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB) ![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white) ![Axios](https://img.shields.io/badge/Axios-5A29E4?style=flat-square&logo=axios&logoColor=white) |
| **Backend** | ![Nodejs](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=Node.js&logoColor=white) ![Express](https://img.shields.io/badge/Express-000000?style=flat-square&logo=express&logoColor=white) |
| **Database** | ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white) ![Sequelize](https://img.shields.io/badge/Sequelize-52B0E7?style=flat-square&logo=sequelize&logoColor=white) |
| **Auth & Tools** | `JWT` `Bcrypt` `Multer` `Git` `Postman` |

<br/>

## 🚀 Key Features

### 1. 완벽한 인증 시스템 (Authentication)
- **JWT (Json Web Token)** 기반의 로그인/회원가입
- **Bcrypt**를 활용한 비밀번호 단방향 암호화 저장
- Access Token 만료 처리를 통한 보안 강화

### 2. 게시글 & 미디어 관리 (CRUD)
- 이미지 업로드 및 미리보기 (**Multer** 활용)
- 게시글 작성, 수정, 삭제 및 최신순 정렬 조회
- 파일명 중복 방지를 위한 난수 생성 로직 적용

### 3. 소통 기능 (Interaction)
- 게시글에 대한 댓글 작성 및 삭제
- **User - Post - Comment** 로 이어지는 1:N 관계형 데이터 구조 설계

<br/>

## 💾 ERD Structure
> User, Post, Comment 테이블 간의 관계를 정의하여 데이터 무결성을 확보했습니다.

*(여기에 ERD 이미지나 스크린샷을 넣어주세요)*

<br/>

## 🔥 Trouble Shooting & Learning
프로젝트를 진행하며 마주친 기술적 문제와 해결 과정입니다.

<details>
<summary><b>1. JWT 만료 시간 설정 오류와 해결</b> (Click to expand)</summary>
<div markdown="1">

- **문제 상황:** `expiresIn` 옵션에 숫자와 문자열을 혼용하여 사용했더니, 토큰 만료 시간이 예상과 다르게 동작하거나 코드 가독성이 떨어짐.
- **해결:** 팀/개인 규칙으로 **"시간 단위는 문자열(예: '60s', '1h')로 통일한다"**는 컨벤션을 정립하여 해결.
- **배운 점:** 라이브러리 공식 문서를 통해 정확한 타입 정의를 확인하는 습관의 중요성.

</div>
</details>

<details>
<summary><b>2. Sequelize Migration과 FK 설정 충돌</b> (Click to expand)</summary>
<div markdown="1">

- **문제 상황:** 모델(Model) 파일과 마이그레이션(Migration) 파일의 FK 옵션이 미세하게 달라 DB 테이블 생성 시 에러 발생.
- **해결:** `ERD 설계 -> Migration 작성 -> Model 정의` 순서로 작업 루틴을 확립하고, `references` 및 `onDelete` 옵션을 양쪽에 동일하게 맞춤.
- **배운 점:** ORM을 쓰더라도 실제 SQL 레벨에서 외래키가 어떻게 작동하는지 이해해야 함.

</div>
</details>

<details>
<summary><b>3. 이미지 파일명 중복 덮어쓰기 문제</b> (Click to expand)</summary>
<div markdown="1">

- **문제 상황:** 같은 이름을 가진 이미지를 업로드하면 기존 파일이 덮어씌워지는 현상.
- **해결:** `Date.now()` 타임스탬프와 난수를 조합하여 고유한 파일명을 생성하는 로직을 Multer 설정에 추가.
- **배운 점:** 파일 시스템 관리 시 네이밍 규칙(Naming Convention)의 중요성.

</div>
</details>

<br/>

## ⚙️ How to Run

**1. Clone the repository**
```bash
git clone [https://github.com/Sarangheayo/saragram.git](https://github.com/Sarangheayo/saragram.git)
cd saragram
