---
title: "알렉사 스킬 만들기 간편 가이드 2편"
date: 2019-12-03 00:16:00 -0400
last_modified_at: 2019-12-03 16:30:00 -0400
categories: Development
tags: alexa
---

### **1편에서는 기본 Default Region Endpoint를 이용하여 code 작성을 해보았습니다.**

### **2편에서는 AWS Lambda를 새로 생성하여 알렉사 스킬에 연결해보는 과정을 진행해보겠습니다.**

# **1.AWS Lambda 생성하기**

AWS Lambda 에 접속하여 콘솔에 로그인 합니다.  
![](assets/images/alexa-guide2/1-1.png "1-1")

위에 있는 서비스 탭에서 -> 컴퓨팅 -> Lambda를 클릭합니다.  
![](assets/images/alexa-guide2/1-2.png "1-2")

왼쪽의 함수 탭을 클릭하여 함수 생성하기 버튼을 누릅니다.  
![](assets/images/alexa-guide2/1-3.png "1-3")

함수 이름을 적고 함수를 생성합니다.  
![](assets/images/alexa-guide2/1-4.png "1-4")

생성이 완료되었습니다.  
![](assets/images/alexa-guide2/1-5.png "1-5")

# **2.Lambda의 트리거에 알렉사 추가하기**

위에서 생성된 Lambda 화면에서 구성 탭-> 블럭으로 되어 있는 + 트리거 추가 버튼을 누릅니다. 트리거 구성에서 Alexa Skills Kit을 선택합니다.  
![](assets/images/alexa-guide2/2-1.png "2-1")

알렉사 디벨로퍼 콘솔 -> 스킬선택 -> 왼쪽의 Endpoint 탭 클릭 -> Your Skill ID를 복사하여 스킬 ID에 붙여넣기하고 Add를 눌러 트리거 추가를 완료합니다.  
![](assets/images/alexa-guide2/2-2.png "2-2")

# **3.알렉사 Endpoint를 AWS Lambda에 연결하기**

맨 위에 적혀있는 ARN을 복사합니다.  
![](assets/images/alexa-guide2/3-1.png "3-1")

알렉사 디벨로퍼 콘솔 -> 스킬선택 -> 왼쪽의 Endpoint 탭 클릭 -> Default Region에 붙여넣기 하고 Save Endpoints를 눌러 저장한 후 build해줍니다.  
![](assets/images/alexa-guide2/3-2.png "3-2")

build 후, Code 탭에 들어가보니 Endpoint가 새로 생성한 Lambda로 변경됐기 때문에, 아래의 코드가 더이상 호스트되지 않는다고 나옵니다.
이제는 여기에 작성된 코드는 더 이상 호출되지 않고 위에서 생성했던 Lambda 함수가 호출될 것입니다.  
![](assets/images/alexa-guide2/3-3.png "3-3")

# **4.AWS Lambda에 코드 업로드하기**

참고 : building-amazon-alexa-skills-nodejs

```
npm 초기화 및 알렉사 모듈 설치
npm init -y
npm install ask-sdk —-s. //알렉사 모듈 설치
```

lastBread.js 생성 후( 파일 명은 바꾸셔도 됩니다. ) Code 탭의 index.js의 내용을 전체 복사하여 붙여넣기 합니다.

프로젝트 구조는 아래와 같습니다.  
/  
-- node_modules  
&nbsp;&nbsp;&nbsp;&nbsp;⌙ 모듈들...  
-- lastBread.js  
-- package.json  
-- package-lock.json

프로젝트의 root 에서 아래의 명령어를 실행하여 zip 파일을 생성합니다.
zip -r lastBread.zip ./node_modules/\* ./lastBread.js

결과  
/  
-- node_modules  
&nbsp;&nbsp;&nbsp;&nbsp;⌙ 모듈들...  
-- lastBread.js  
-- package.json  
-- package-lock.json  
-- lastBread.zip

다시 Lambda 화면으로 돌아와서 구성탭 -> 함수 코드 -> Code Entry type을 ".zip 파일 업로드”로 선택하고 위에서 생성한 lastBread.zip파일을 업로드합니다. 그리고 핸들러 영역에서 lastBread.js가 메인파일이기 때문에 module name을 lastBread로 변경하여 lastBread.handler 라고 입력해줍니다. 마지막으로, 맨위의 Save 버튼을 눌러 저장합니다.  
![](assets/images/alexa-guide2/4.png "4")

# **5.테스트**

다시 알렉사 디벨로퍼 콘솔로 와서 테스트를 해보면 정상적으로 응답이 오는 것을 확인하실 수 있습니다.  
![](assets/images/alexa-guide2/5.png "5")

지금까지 람다 함수 생성부터 람다<->알렉사 연결 과정, 람다 코드 업로드까지 전체적인 과정을 다뤄봤습니다.  
이상으로 알렉사 스킬 만들기 간편 가이드2 편을 마치겠습니다. 감사합니다.
