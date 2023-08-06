<br/>
<br/>

<p align="center">
<img src="https://files.cloudtype.io/logo/cloudtype-logo-horizontal-black.png" width="50%" alt="Cloudtype"/>
</p>

<br/>
<br/>

# Prisma(Next.js)

Next.js 기반에 Prisma ORM을 적용한 템플릿입니다.
## 🖇️ 준비 및 확인사항

### 지원 Node 버전
- Prisma는 최소 14.17.0 버전의 Node를 필요로 합니다.
- Next.js는 최소 14.6.0 버전의 Node를 필요로 합니다.
- ⚠️ 로컬/테스트 환경과 클라우드타입에서 설정한 Node 버전이 상이한 경우 정상적으로 빌드되지 않을 수 있습니다.


### 빌드인자 및 환경변수 설정
Next.js 어플리케이션을 배포하는 경우 빌드 시점에 외부의 값을 주입하는 것과 런타임 시점에 값을 참조하는 경우를 구분하여 빌드인자 혹은 환경변수를 세팅해야 합니다.
- 빌드인자(Build Arguments): 빌드 시 인자의 값이 주입
- 환경변수(Environment Variables): 런타임 시점에 값을 참조


### 필요 파일
- Prisma를 어플리케이션과 연동하여 클라우드타입에 배포하기 위해서는 package.json 의 npm script가 알맞게 작성되어 있어야 합니다. Prisma의 경우 데이터베이스 스키마 마이그레이션이 어플리케이션 빌드 과정 중에 수행되기 때문에 올바르지 않은 Build 스크립트 작성 시 정상적으로 구동되지 않을 수 있으며, 배포 시 package.json에서 정의한 내용에 따라 Build Command 필드에 알맞은 값을 입력해주어야 어플리케이션이 정상적으로 동작합니다.
- Prisma는 Prisma Studio 라는 툴을 통해 데이터베이스의 데이터를 조회 및 조작할 수 있는 기능을 제공하고 있습니다. 이 기능을 사용하시려면 어플리케이션이 배포되는 포트 뿐만 아니라 Prisma Studio가 서비스되는 5555 포트를 배포 시에 반드시 추가해주어야 합니다. Next.js 어플리케이션과 Prisma Studio를 동시에 서비스 하기 위해 예제에서는 npm 패키지인 concurrently 가 사용되었습니다.


  ```json
  {
    "name": "next-prisma",
    "version": "1.0.0",
    "description": "",
    "keywords": [],
    "license": "MIT",
    "author": "",
    "main": "index.js",
    "scripts": {
      "dev": "next",
      "build": "prisma generate && prisma migrate deploy && prisma db seed && next build",
      "start": "concurrently \"next start\" \"npx prisma studio\"",
      "studio": "npx prisma studio"
    },
    "dependencies": {
      "@prisma/client": "^4.11.0",
      "next": "^13.0.0",
      "react": "^18.0.0",
      "react-dom": "^18.0.0",
      "react-markdown": "^8.0.0"
    },
    "devDependencies": {
      "concurrently": "^7.6.0",
      "prisma": "^4.11.0"
    },
    "prisma": {
      "seed": "node prisma/seed.js"
    }
  }
  ```



## 💬 문제해결

- [클라우드타입 Docs](https://docs.cloudtype.io/)

- [클라우드타입 FAQ](https://help.cloudtype.io/guide/faq)

- [Discord](https://discord.gg/U7HX4BA6hu)


## 📄 License

### Prisma
- [Apache 2.0](https://github.com/prisma/prisma/blob/main/LICENSE)

### Next.js
- [MIT](https://github.com/vercel/next.js/blob/canary/license.md)