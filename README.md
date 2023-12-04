# MOIZA-MSA

**MOIZA**는 여러 사람들의 스케줄을 종합하여 모임 일정을 결정해주는 서비스입니다. 
이 서비스를 통해 참여자들은 자신의 일정을 입력하고, MOIZA는 이를 종합하여 가장 적합한 모임 일정을 제안합니다. 
MOIZA는 가장 많은 참여자들이 참여 가능한 시간대를 찾아내고, 이를 바탕으로 최적의 일정을 선정합니다.
이를 통해 모임을 조직하는 데 필요한 번거로움을 줄이고, 효율적인 일정 관리를 도와줍니다.

## 사용예시

**1.모임 일정의 범위, 진행 기간 등을 정하여 모임 생성**<br/>

_예시에서는 1월 10 ~ 12일까지, 13시부터 19시20분까지 일정의 범위가 설정됨._<br/>
_최종 모임 일정은 이 범위 내에서 결정됨._<br/>
<img width="375" alt="Frame 1 (1)" src="https://github.com/jzakka/MOIZA-MSA/assets/105845911/ffe13189-d7a7-4169-ac3a-a75f0fab344d">

<br/>

**2.참여자가 참여희망 날짜 선택**<br/>
<img width="220" alt="Frame 3" src="https://github.com/jzakka/MOIZA-MSA/assets/105845911/e698473c-ea99-4385-ab5f-cc25fa1e6bf3">

<br/>

**3.참여 희망 시간 선택**<br/>
<img width="324" alt="Frame 2 (1)" src="https://github.com/jzakka/MOIZA-MSA/assets/105845911/a9d02eab-a677-421f-b921-f6116fe534cf">

<br/>

**4.모임 일정 조율 기간이 끝나고 모임일정 확정**<br/>
> 확정된 모임 일정은 가장 많은 참여자들이 참여가능한 시간이다.
<img width="392" alt="Frame 4" src="https://github.com/jzakka/MOIZA-MSA/assets/105845911/d30e812b-faae-4db7-830e-8917325ccaf7">

## 아키텍처구조

![moiza_msa_architecture](https://github.com/jzakka/MOIZA-MSA/assets/105845911/b92d382a-694c-47bc-bb43-84fd4471b870)


## API

|**URL**|**Method**|**Description**|
|---|---|---|
|[/gather-service/gathers](https://github.com/jzakka/gather-service/blob/f762e6c84ae1777e6cb62c9f29a2873dc226ce8b/apidocs/CREATE.md)|`POST`|모임 생성|
|[/gather-service/gathers/:gatherId](https://github.com/jzakka/gather-service/blob/f762e6c84ae1777e6cb62c9f29a2873dc226ce8b/apidocs/GETGATHER.md)|`GET`|단일 모임 조회|
|[/member-service/members/:memberId](https://github.com/jzakka/member-service/blob/937661df2a70ed628d08e3e7c7fdbd3f2050e54b/apidocs/GETMEMBER.md)|`GET`|단일 회원 조회|
|[/member-service/members](https://github.com/jzakka/member-service/blob/937661df2a70ed628d08e3e7c7fdbd3f2050e54b/apidocs/SIGNUP.md)|`POST`|회원가입|
|[/member-service/login](https://github.com/jzakka/member-service/blob/937661df2a70ed628d08e3e7c7fdbd3f2050e54b/apidocs/LOGIN.md)|`POST`|로그인|
|[/join-service/joins](https://github.com/jzakka/join-service/blob/cd195222b18f449225ae5c57c36a90d91a6e83af/apidocs/JOIN.md)|`POST`|모임 참여|
|[/join-service/:gatherId/joins](https://github.com/jzakka/join-service/blob/cd195222b18f449225ae5c57c36a90d91a6e83af/apidocs/GETJOINS.md)|`GET`|모임 참여자 조회|
|[/join-service/joins/:memberId](https://github.com/jzakka/join-service/blob/cd195222b18f449225ae5c57c36a90d91a6e83af/apidocs/GETJOINEDGATHERS.md)|`GET`|참여한 모임 조회|
|[/join-service/joins](https://github.com/jzakka/join-service/blob/cd195222b18f449225ae5c57c36a90d91a6e83af/apidocs/CHANGETIME.md)|`PATCH`|참여 시간 수정|
|[/join-service/joins](https://github.com/jzakka/join-service/blob/cd195222b18f449225ae5c57c36a90d91a6e83af/apidocs/CANCELJOIN.md)|`DELETE`|모임 참여 취소|
|[채팅 전송 웹소켓 URL](https://github.com/jzakka/chat-service/blob/4673dbc6846d0585984faa1096f581534b5f8c7f/apidocs/SENDCHAT.md)|STOMP METHOD|채팅 송수신|
|[/chat-service/chats/:gatherId](https://github.com/jzakka/chat-service/blob/4673dbc6846d0585984faa1096f581534b5f8c7f/apidocs/SENDCHAT.md)|`GET`|채팅방에서 채팅 더 불러오기|

## issue archive

- [JPA 연관관계 삭제 N+1](https://velog.io/@mouse4786/JPA-%EC%97%B0%EA%B4%80%EA%B4%80%EA%B3%84%EA%B0%84-%EC%82%AD%EC%A0%9C-%EC%A3%BC%EC%9D%98%EC%A0%90)
- [확장성을 고려한 채팅 서비스](https://velog.io/@mouse4786/%EA%B0%9C%EC%9D%B8-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EC%B1%84%ED%8C%85-%EC%84%9C%EB%B9%84%EC%8A%A4%EC%9D%98-%EA%B5%AC%ED%98%84)
- [httpservlet request바디는 컨트롤러에서만 읽자](https://velog.io/@mouse4786/%EA%B0%9C%EC%9D%B8-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-mvc-%EC%9D%B8%ED%84%B0%EC%85%89%ED%84%B0)
- [채팅 비동기 처리](https://velog.io/@mouse4786/%EC%B1%84%ED%8C%85-%EA%B8%B0%EB%8A%A5-%EC%84%B1%EB%8A%A5-%EA%B0%9C%EC%84%A0)
