---
우선 layout: default
title: installation
permalink: /nextJSTutorial/installation/
---

## installation

## installation?

이번 단계는 next.js 환경을 구축할 수 있도록 설치하는 과정입니다.

## system requirements

해당 과정을 진행하기 위해선 아래와 같은 것들이 요구됩니다.

- 18.18 이상의 버전인 node.js
- macOS, Windows(WSL이 포함된), Linux

## 자동 installation

빠르게 next.js application을 개발하기 위해 [npx]({{'/npx/' | relative_url }})를 통해 create-next-app 명령어를 입력하겠습니다.

아래와 같은 명령어를 terminal에 입력하면 됩니다.

```
npx create-next-app@latest
```

## 수동 installation

수동으로 nex.js application을 개발하고 싶다면, 필요한 패키지를 설치해야 합니다. 아래에 작성한 명령어를 입력하여 설치할 수 있습니다.

```
npm i next@latest react@latest react-dom@latest
```

설치가 되었다면, PACAKAGE.JSON 파일에 아래의 명령어들을 추가해야 합니다.

```
{
  "scripts": {
    "dev": "next dev --turbopack",
    "build": "next build",
    "start": "next start",
    "lint": "eslint"
  }
}
```

이 스크립트들은 아래와 같은 의미를 가지고 있습니다.

- `next dev --turbopack`: turbopack(로컬 개발속도 개선을 위해 next.js에 통합된 형태로 사용될 수 있게 설계된 번들러입니다.)을 사용하여 개발 서버를 시작합니다.
- `next build`: 애플리케이션을 빌드합니다.
- `next start`: 서버를 시작합니다.
- `eslint`: ESLint(작성한 자바스크립트 코드의 코드 스타일과 문법을 검사해주는 도구입니다.)를 실행합니다.

## app directory 구성하기

Next.js는 file-system routing을 사용하기 때문에, file을 어떻게 구성하는지에 따라 application의 경로가 결정됩니다.

```
export default function RootLayout({
  children,
}: {
  children: React.ReactNode
}) {
  return (
    <html lang="en">
      <body>{children}</body>
    </html>
  )
}
```

위와 같이 app 폴더를 만든 후 layoiut.tsx 파일을 생성한 후 내용을 작성했습니다. layout.tsx는 root layout입니다. root layout은 꼭 있어야 하며, html tag와 body tag가 포함되어야 합니다.

아래와 같이 간단한 페이지를 하나 생성했습니다.

```
export default function Page() {
  return <h1>Hello, Next.js!</h1>
}
```

layout.tsx와 page.tsx 모두 application의 root 경로를 방문할 때 마다 redering 됩니다.

만일 root layout을 생성하는 것을 잊어버린 상황이라면 아래와 같은 명령어를 실행하면 자동으로 파일이 생성된 후 server가 구동된다고 합니다.

```
next dev
```

project의 root에 존재하는 src folder를 사용하여 application code와 configure file을 분리하는 것 또한 가능하다고 합니다.

## 공용 folder 생성하기(필수적이진 않습니다.)

project의 root에 공용 folder를 만들어서 image, font와 같은 static한 파일을 넣어둘 수 있습니다. public folder 내부의 파일은 root url로 시작되는(/)에서 시작하는 코드로 사용할 수 있습니다. 아래의 예시와 같이 말입니다.

```
import Image from 'next/image'

export default function Page() {
  return <Image src="/profile.png" alt="Profile" width={100} height={100} />
}
```

Image tag의 src 값으로 들어간 경로를 확인해보시면, root directory 값을 입력한 것을 확인할 수 있습니다.

## dev server 실행

npm run dev를 실행하여 dev server를 실행할 수 있습니다.
