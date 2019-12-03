---
title: "알렉사 스킬 만들기 간편 가이드 1편"
date: 2019-12-03 00:15:00 -0400
last_modified_at: 2019-12-03 16:20:00 -0400
categories: Development
tags: alexa
---

# **시작하기**

[알렉사 스킬 가이드](https://developer.amazon.com/docs/custom-skills/steps-to-build-a-custom-skill.html)

## **1.스킬 생성하기**

#### [알렉사 콘솔](https://developer.amazon.com/alexa/console/ask)에 접속하여 Create skill 버튼을 누릅니다.

![](/assets/images/alexa-guide1/1-1.png "1-1")

#### Skill name : 알렉사에 등록할 스킬 이름을 입력합니다.

#### Default language : 알렉사에 사용할 언어를 선택합니다.

#### Custom 모델과 Alexa-Hosted 서버(추천)를 선택하고 Create skill 버튼을 눌러 스킬을 생성합니다.

![](/assets/images/alexa-guide1/1-2.png "1-2")  
![](/assets/images/alexa-guide1/1-3.png "1-3")

## **2.Invocation Name 등록하기**

#### 스킬등록이 완료 되었으면 아래와 같은 화면이 나옵니다.

#### 왼쪽의 Invocation 탭에서 Skill Invocation Name을 2단어 이상으로 등록하고 Save Model 버튼을 눌러 저장합니다.

#### Invocation Name은 알렉사에서 특정 스킬을 호출할 때 부르는 이름입니다.

#### 예를 들어, “알렉사, 라스트 브레드에서 매칭 시작” 라고 말했을 때 ‘라스트 브레드’가 Invocation Name입니다.

![](/assets/images/alexa-guide1/2.png "2")

## **3.Intent 등록하기**

#### intent는 사용자의 발화에 대해, 특정 기능을 수행하도록 합니다. 예를 들어, “알렉사, 라스트 브레드에서 매칭 시작해줘”라고 말했을 때 “매칭 시작해줘”라는 Intent를 통해 사용자가 매칭을 하고 싶어하는 것을 알 수 있고 이것은 특정 기능을 수행하게 합니다. 그러면 server에서는 “매칭을 시작합니다.”와 같은 적절한 응답 및 동작을 진행할 수 있습니다.

#### 처음 생성되어 있는 HelloWorldIntent를 MatchingStartIntent로 바꿔서 등록해보겠습니다.사용자들은 게임을 시작하기 위해 “매칭 시작”, “게임 시작”, “시작” 등의 발화를 할 것이므로 아래와 같이 사용자들의 예상 발화들을 등록해놓습니다. 마지막으로 Save Model 버튼을 눌러 저장하고 Build Model 버튼을 눌러 해당 버전을 빌드합니다.

![](/assets/images/alexa-guide1/3.png "3")

## **4.Endpoint**

#### 왼쪽 탭에서 Endpoint를 클릭합니다. Endpoint는 사용자가 Alexa Skill과 상호 작용할 때 POST 요청을 수신하여 데이터를 처리하여 응답하는 서버입니다. 이 Endpoint를 활용하여, 사용자에게 적절한 응답을 해줄 수 있습니다. 여기 적혀있는 Default Region을 활용하면 Code 탭에서 람다 함수를 바로 수정하여 적용할 수 있습니다.

![](/assets/images/alexa-guide1/4.png "4")

## **4-1.Endpoint Code 수정**

#### Code 탭에 있는 index.js는 aleax의 endpoint에 연결되어 있는 함수 입니다. 아래의 HelloWorldIntentHandler를 MatchingStartintentHandler로 수정해보겠습니다. 아래처럼 HelloWorldIntentHandler를 MatchingStartintentHandler로 변경하고 주석부분도 알맞게 수정합니다.

![](/assets/images/alexa-guide1/4-1-1.png "4-1-1")

#### 마지막으로 맨 아래에 있는 exports.handler 에서도 HelloWorldIntentHandler를 MatchingStartintentHandler로 변경해줍니다. 변경 완료 후 Save 버튼을 눌러 저장하고 Deploy 버튼을 눌러 배포해줍니다.

![](/assets/images/alexa-guide1/4-1-2.png "4-1-2")

## **5.테스트**

#### Test 탭에서 아래와 같이 테스트해봅니다.

![](/assets/images/alexa-guide1/5.png "5")

#### "matching start"라고 했을 때, MatchingStartIntent가 실행되어 "Start matching" 이라는 응답이 잘 오는 것을 확인할 수 있습니다. 지금까지 스킬 생성부터 Invocation name 등록, 인텐트 등록, Endpoint Code 수정, 마지막으로 Test 까지 진행해보았습니다. 하지만 Default Region Endpoint의 람다 함수를 사용하는 것은 외부 모듈의 사용에 한계가 있기 때문에 다음 2편에서는 AWS의 Lambda와 연결해서 사용하는 방법을 알아보겠습니다.

##### 더 자세한 내용들은 [공식문서](https://developer.amazon.com/docs/ask-overviews/build-skills-with-the-alexa-skills-kit.html)에 나와있습니다.
