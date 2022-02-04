### Dialogflow로 챗봇 만들기 (1) - entity 정의, 생성 

오른쪽 상단에는 create entity가 있는데 먼저 STUDENT_INFO를 생성한 후, entity에는 value 값으로 예를 들어 과일이라는 entity가 있다면
value 값으로는 "사과","오렌지","레몬","포도" 등 여러개의 과일을 가지도록 할 것입니다. Entity는 보통 하나의 value 값에 여러개의 동의어를 넣어 value 값을 통일해주는 역할을 합니다.



예를 들어, "세종시","세종","세종특별자치시" 는 모두 "세종"의 값과 동일한 동의어라고 사전에 정의할 수 있습니다. 그렇게 되면 value 값이 분리되지 않고 "세종"으로 통일 될 수 있습니다.



![엔티티생성](https://user-images.githubusercontent.com/62290451/152479809-19ad8897-ffc8-484f-b37f-1690796c2b9a.png)




위에는 이해를 돕기위해 과일, 지역을 사용하였는데 제가 만들고자 하는 챗봇은 학교 정보를 제공해주는 챗봇이기 때문에 
수강신청 날짜의 value 값으로는 수강신청, 수강신청날짜, 수강신청 시간, 수강신청기간, 수강신청일 등 student_info에는 
학교 정보와 관련된 entity와 각 value값들을 정의했습니다. 


Regexp entity : 정규표현식을 이용하여 정의하는 방법



Allow automated expansion : 자동적인 확장입니다. 반복되는 내용에 대해 계속 정의하지 않고 자동적으로 처리해줍니다. 예를 들어, 1, 2, 3, 4와 같은 시퀀스를 가지는 entity에 대해서 유용하게 사용할 수 있습니다.



Fuzzy matching : 사전에 정의했던 value와 스펠링이 정확히 일치하지 않아도 매칭시켜주는 옵션
 
 
 
 
작성이 완료되면 우측 상단 SAVE 버튼을 눌러 마무리 합니다. 

## intent에 적용 

intent 탭으로 이동하여 CREATE INTENT 버튼을 클릭하여 작성합니다. intent이름은 class_request로 하겠습니다.




![인텐트](https://user-images.githubusercontent.com/62290451/152481002-b03dab53-0977-4243-9f94-9285ed6d5e13.png)




Training phrases 섹션에 학습문구를 입력합니다. Dialogflow 공식 문서에서는 10~20개의 학습문구를 권장하지만, 지금은 10개 정도의 학습문구를 입력하겠습니다.
"수강신청일 언제야"라고 입력하면 Dialogflow에이전트가 자동으로 "수강신청"이라는 entity를 포착해 냅니다. 만약, 해당 entity를 자동으로 포착하지 않는다면 "수강신청"이라는 부분을 마우스 드래그를 해서
entity를 선택할 수도 있습니다. 




![인텐트 답변](https://user-images.githubusercontent.com/62290451/152481305-9cd41e0a-1a71-4988-b12e-c831f9564784.png)




responses섹션으로 가서 class_request에 대한 답변으로 위에 사진처럼 답변을 입력합니다. 답변까지 입력하였다면 우측 상단 SAVE버튼을 눌러 에이전트가 intent를 학습하도록 합니다.




![테스트](https://user-images.githubusercontent.com/62290451/152481668-ddf522e5-d082-4604-bad1-b91927083b88.png)



"수강신청일 언제야" 뿐만이 아니라 다른 "수강신청 기간" 이라고 입력해도 같은 결과가 나오게 됩니다. 
entity는 이처럼 여러 값들을 가지는 개념을 한데로 모아 intent를 작성에 편리함을 주기도 하지만, 사전에 정의된 parameter에 대해서 value를 포착해 답변에 영향을 줄 수 도 있습니다.
위 intent처럼 다양한 학교 정보 수강신청, 수강변경, 휴학, 복학 등 확장해나갈 수 있습니다. 
