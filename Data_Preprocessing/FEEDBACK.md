# 피드백 남기는 곳

## 심소은
Titanic

le =  LabelEncoder() 를 사용하면 deck의 'Unknown'이 알파벳 순서대로 인코딩되서 순서가 생기는데 이 경우는 순서가 없는 변수에서는 원핫 인코딩을 적용하면 좋을거같아.


Iris

마지막에 y_pred = lr.predict(X_test) 이렇게 X_test로 예측했는데 보면 스케일링을 위에서 한 걸 사용하면 더 좋을거같아.


Wine

마지막 셀 그래프가 좋은데 이 그래프로 어떤 결과를 얻어가면 좋을까?

## 우유정
Titanic

결측치 시각화(msno.matrix)와 기초 통계 확인까지는 깔끔하지만, 중간 이후 데이터프레임 출력 셀들에 대한 핵심 인사이트나 전처리 방향을 설명하는 마크다운(주석)을 보충해 주면 분석 의도를 파악하기 훨씬 좋을 것 같음.

Iris

마지막 셀에서 X_train은 스케일링된 배열(X_train_std)을 넣었으나 X_test는 스케일링되지 않은 원본 데이터프레임(X_test)을 그대로 예측에 사용해 피처 이름 불일치 경고와 데이터 누수/스케일 불일치가 발생했으니 X_test_std = s.transform(X_test)로 변환 후 평가해야함.

Wine

규제 강도(C) 변화에 따른 가중치 변화를 시각화할 때 df.columns에 타겟 변수인 'class'까지 포함되어 범례에 함께 출력되고 있으므로, 피처 컬럼(df.columns[:-1])만 지정해 주면 그래프가 더 정확해질 것 같음.

## 이도연
Titanic

embarked, embarked_town이 nan인 행을 최빈값으로 대체하는 대신 제거함으로써 왜곡이 비교적 적도록 하였으며 

학습셋 테스트셋 분리 및 표준화(StandardScaler)하여 로지스틱 회귀까지 실행 및 결과 확인 : 실제 학습과정을 위한 데이터 처리 과정이므로, 데이터 처리의 목표가 확실함

주석:

```python
#df.dropna(subset=['embarked'])
#df.dropna(subset=['embark_town'])

df = df.dropna(subset=['embarked'])
df = df.dropna(subset=['embark_town'])
```

위와 같이 수정이 필요해 보임 (이전 코드는 dropna가 df에 실제로 적용 안될 것으로 예상)

<br/>

Iris

stratify로 클래스 비율 유지하고 scaler를 train에만 fit한 점이 좋았음 (데이터 누수 방지)

주석: lr.predict(X_test)에 스케일링 안 된 X_test가 들어가 있어서 X_test_s로 바꿔야 할 것 같음

Wine

L1 규제 C 변화에 따른 가중치 변화로 영향력 큰 변수를 확인하는 접근이 좋았음

주석: label이 df.columns[column+1]이라 변수명이 한 칸씩 밀려 있음 (마지막 변수가 class로 표시됨). df.columns[column]으로 수정 필요해 보임




각 데이터셋별 피드백이 아니라 전체 내용에 대한 피드백이면 지우고 작성해주셔도 됩니다.
