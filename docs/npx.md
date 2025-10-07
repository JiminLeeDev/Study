---
layout: default
title: npx
permalink: /npx/
---

# npx

## npx?

npx는 npm 패키지를 설치하지 않은채로 실행시킬 수 있도록 도와주는 도구입니다. 기본적으로 Node.js를 설치하면 npm과 함께 자동으로 npx도 설치됩니다.

```
npx create-react-app my-app
```

위와 같은 명령어를 terminal에 입력할 경우 create-react-app package를 임시로 다운로드 한 후 실행한 후에 삭제합니다. 그렇기 때문에 재사용할 기능이 아닌 것들은 npx를 통해 설치하는 것이 좋습니다.

## 작동과정

npx는 명령을 실행할 경우 다음과 같은 순서를 거치게 됩니다.

1. 로컬 node_modules/.bin 폴더에 입력한 명령어가 있는지 확인
2. 없다면 전역 npm 패키지에 있는지 확인
3. 명령어가 확인되지 않을 경우 npm registry에서 임시다운로드

## npx vs npm

npm이 패키지를 설치 및 관리하는 도구라면 npx는 패키지를 실행하는 도구입니다. 재사용치 않을 것들은 npx를 통해 실행하고, 재사용할 필요가 있는 것은 npm을 통해 설치하는 것이 좋습니다.

<footer>
© 2025 Jimin Lee
</footer>
