# 주차수요예측
- 데이터출처 : Dacon, LH
- 기간       : 2021.08.30 ~ 2021-09.??
- 분석목적, 데이터설명 : [설명링크](https://dacon.io/competitions/official/235745/data)
- 분석툴     : google colab, sklearn
# 프로세스
- 데이터수집
    - 구글드라이브 연동   
- 데이터전처리 
    - null 값처리
    - 단계화
    - 파생변수 생성, 변수변환  
    - 원핫인코딩
    - 데이터그룹화
    - 왜곡확인
    - 데이터분할
- 모델생성
- 결과갑처리

# 문제점 정리
1. data leakage / one-hot encoding  

    상황(what)     
            - 앞으로 무엇이 올지 모르는 test데이터에 대해서 어떻게 one hot encoding 을 진행할 것인가  
        
    문제점(why)  
            - 대회처럼 test와 train이 구분되어져 있는 경우에는 당장 모델이 쓸모 있는 것처럼 보이나, 실질적으로 test와 train을 합쳐서 원핫인코딩을 진행하는 경우는 data leakage이다. 그 이유는 미래에, 앞으로 올 데이터는 이제까지 없던 데이터가 올 수 있는데 도메인 명확하게 고정되지 않는 이상 합쳐서 진행하면 안됨.  
    해결책(how)  
            - sklearn 데이터인코딩 진행시 unknown 설정을 하면, 해당 row는 모두 0으로 처리됨.
