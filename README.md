# Node.js & React 백엔드 구축 가이드

## 목차

1. [Node.js 세팅 및 서버 구동](#1-nodejs-세팅-및-서버-구동)  
2. [Express 라우팅 및 API 설계](#2-express-라우팅-및-api-설계)  
3. [Sequelize 모델 및 관계 설정](#3-sequelize-모델-및-관계-설정)  
4. [백엔드 필수 패키지 설정](#4-백엔드-필수-패키지-설정)  

---

## 1. Node.js 세팅 및 서버 구동

- Node.js는 자바스크립트 런타임 환경으로, 백엔드 서버를 비동기 방식으로 구현할 수 있습니다.
- NPM은 Node의 패키지 관리 도구입니다.

### 1-1. 설치 및 초기화

1. Node.js LTS 버전 설치: [https://nodejs.org](https://nodejs.org)  
2. 설치 확인:

```bash
node -v
npm -v
```

3. 프로젝트 폴더 생성 및 초기화:

```bash
mkdir back
cd back
npm init
```

### 1-2. PowerShell 실행 오류 해결

```text
npm : 이 시스템에서 스크립트를 실행할 수 없습니다...
```

#### 해결 방법:

```powershell
Get-ExecutionPolicy
Set-ExecutionPolicy RemoteSigned
```

### 1-3. 실습

```bash
// app1.js 파일 작성 후 실행
node app1.js
```

---

## 2. Express 라우팅 및 API 설계

- Express는 라우팅 및 미들웨어 구성이 쉬운 Node.js 웹 프레임워크입니다.

### 2-1. 설치 및 기본 서버

```bash
npm install express
```

- `app.js` 생성 후 `node app.js`로 실행  
- Postman을 통해 API 테스트

### 2-2. HTTP 메서드 설명

| 메서드     | 설명                             |
|------------|----------------------------------|
| `GET`      | 데이터 조회                      |
| `POST`     | 데이터 생성                      |
| `PUT`      | 전체 업데이트 (거의 사용하지 않음) |
| `PATCH`    | 부분 업데이트                    |
| `DELETE`   | 데이터 삭제                      |

### 2-3. 실습 및 폴더 구조

- `/routes` 폴더에 다음 파일 생성:

```
routes/
├── user.js
├── post.js
└── posts.js
```

#### user.js 예시

```js
// POST /user -> 회원가입
// POST /user/login -> 로그인
// GET /user -> 사용자 정보 { id: 1, email: 'one@gmail.com' }
// POST /logout -> 로그아웃
```

#### post.js

```js
// POST /post -> 글 작성
```

#### posts.js

```js
// POST /posts -> 페이징 처리
```

---

## 3. Sequelize 모델 및 관계 설정

### 3-1. 설치

```bash
npm install sequelize sequelize-cli mysql2
```

### 3-2. 초기화 및 설정

```bash
npx sequelize init
```

- `config/config.json` 에서 DB 설정
- MySQL에서 `node_react` 데이터베이스 생성

### 3-3. 모델 구조

#### 1) User 모델

```js
// 필드: id, email (unique), nickname (unique), password
// 관계:
// - User hasMany Posts
// - User hasMany Comments
// - User belongsToMany Posts (as: liked)
// - User belongsToMany Users (as: followers, followings)
```

#### 2) Post 모델

```js
// 필드: id, content
// 관계:
// - Post hasMany Comments
// - Post hasMany Images
// - Post belongsTo User
// - Post belongsToMany Hashtags
// - Post belongsToMany Users (as: Likers)
```

#### 3) Image 모델

```js
// 필드: id, src
// 관계: belongsTo Post
```

#### 4) Comment 모델

```js
// 필드: id, content
// 관계: belongsTo User, belongsTo Post
```

#### 5) Hashtag 모델

```js
// 필드: id, name
// 관계: belongsToMany Posts
```

### 3-4. 관계 요약

- **1:N** → hasMany / belongsTo  
- **N:M** → belongsToMany (중간 테이블 필요)  
- **팔로우 시스템 예시**  
  - 팔로우: followers (나를 보는 사람)  
  - 팔로잉: followings (내가 보는 사람)

### 3-5. DB 초기화

```bash
npx sequelize db:create
node app.js
```

---

## 4. 백엔드 필수 패키지 설정

### 4-1. 서버 자동 재시작 - nodemon

```bash
npm install -D nodemon
```

### 4-2. 비밀번호 암호화 - bcrypt

```bash
npm install bcrypt
```

### 4-3. CORS 허용 - cors

```bash
npm install cors
```

### 4-4. 인증 처리 - passport

```bash
npm install passport passport-local
```

### 4-5. 세션 및 쿠키 관리

```bash
npm install express-session cookie-parser
```

### 4-6. 환경 변수 관리

```bash
npm install dotenv
```

### 4-7. 파일 업로드

```bash
npm install multer
```

### 4-8. 요청 로깅 및 모니터링

```bash
npm install morgan
```

---

## ✅ 실습 문제 정리

1. `node_react2025_ex` 폴더 생성  
2. `back/` 폴더로 이동  
3. `npm init` (프로젝트명: `node_ex`)  
4. Express 설치  
5. `/routes` 폴더에 `user.js`, `post.js`, `posts.js` 생성  
6. API 작성 후 `app.js`에 연결하여 서버 구동  

---

이 문서는 Node.js 백엔드 서버를 Express + Sequelize 기반으로 구성하는 입문 가이드입니다. 필요한 경우 단계별 예제 코드나 추가 설명도 제공 가능합니다.
