---
title:  "데이터 마이닝 - EDA"
categories:
  - data mining
tags:
  - data mining
  - EDA
---
최대한 수식을 배제하고 전체적인 흐름을 익히게 했습니다

따라서 궁금하신 점은 메일이나 검색을 활용해주세요

이번 글은 데이터 마이닝의 시작 단계에서 배우는 **EDA(Exploratory Data Analysis)** 에 관한 글입니다.

## EDA란 

EDA란 탐색적 자료 분석, 즉 데이터가 어떤 자료로 구성되어있고 분포는 어떠한지를 보는 것입니다. 

EDA라는게 왜 나왔냐면, 데이터베이스나 엑셀 등등에 저장된 데이터를 숫자로만 보게되면 매우 지루하고 자세하게 보지도 못하기 때문에

조금더 데이터를 잘파악하도록 하고자 하는 노력에서 나왔습니다. 

==따라서 정해진 방식이 아니라 만약 데이터를 더 잘 파악할 수 있다면 여러분들의 창의력을 발휘해 데이터를 표현해도 됩니다==하

## EDA 목적

* Detection of mistakes (데이터 수집단계에서 실수로 입력한 부분이 있는지)
* Checking of assumptions (데이터에 대한 가정이 맞는지)
* Preliminary selection of appropriate models (데이터 유형에 맞는 적절한 모델 선택하기)
* determining relationships among explanatory variables (설명변수들 사이의 관계 파악하기)
* assessing the direction and rough size of relationships between explanatory and outcome variables. (설명변수와 목적변수 사이의 관계 파악)

==한가지 잊지 말아야 할것은 우리가 가진 데이터는 sample 데이터이므로

우리는 sample 데이터를 통해 단지 population 분포와 parameter를 파악한다는 것에 주목해야합니다.==

## Type of EDA

기본적으로 EDA는 4가지 타입으로 구분할 수 있습니다.

그림으로 표현하느냐 글로 표현하느냐 등으로 말이죠.

### Type of EDA - Graphical or non-graphical

먼저 그림으로 데이터를 표현하느냐 아니면 숫자 등으로 표현하느냐 입니다.

데이터를 그림으로 표현하게 되면 한눈에 데이터를 파악할 수 있으므로 개략적인 형태를 파악할 수 있습니다.

그렇다면 언제 그림이 아닌 숫자로 표현할까요?

바로 데이터의 평균이나 분산 등과 같은 정확한 값이 필요할때입니다.

### Type of EDA - Univariable or Multivaliable

이것은 변수를 하나씩 확인 할 것인지 아니면 여러 변수를 동시에 확인 할 것인지 여부 입니다.

==여기서 중요한 것은 여러 변수를 동시에 확인하기전에 무조건 개별 데이터 먼저 파악 해보아야한다는 것입니다.==

## Univariable, non-graphical

-outlier detection

우리가 변수를 볼 떄, 파악 해야 할것은 수집된 데이터들은 모두 다 샘플데이터라는 것입니다.

샘플데이터가 모집단의 변수를 잘 나타낼 수도 있고 그러지 않을 수도 있는데 

중요한 것은 여기서 우리가 해야될 일은 바로

==샘플 분포를 잘 파악해서, 모집단의 분포가 어떨 것인가를 생각해야한다는 것입니다.==

### Univariable, non-graphical - Categorical data

**범주형 변수로 데이터를 수집한 이유**

* 값의 범위에 관심이 있어서
* 빈도에 관심이 있어서

**표현 방법**

Tabulation(빈도표)
|            | 남자      | 여자      |
|--------    |--------   |--------  |
| Count      |     7     |3         | 
| Proportion |   0.7     |0.3       |
| Percent    |      70%  |30%       |

여기서 count와 proportion, percent는 서로 바꿔쓸수 있으므로 상황에 맞게 사용하면 됩니다.

**알수있는것**

* missing data가 존재한다면 percent의 합이 100%가 안되므로 missing data 파악가능
* 데이터의 갯수 파악가능, 구성비 파악가능

### Univariable, non-graphical - Quantitative data

**양적변수로 Univariable EDA 하는 이유**
* 샘플 데이터를 통해 모집단의 분포를 평가가능 - center, spread, modality, shape, outliers, skewness, and kurtosis 
> 이런 값들은 categorical variable에서는 아무 의미가 없습니다.

* 단지 히스토그램으로 그려서 파악 가능한 분포보다 우리가 관심있어하는 변수에 대해 더 자세하게 알 수 있게됨

**표현방법**

sample statistics (모집단 값이라고 추정되는 값)로 표현합니다

* Central tendancy - sample mean, sample median, mode(peak, unrepresentative of the central tendency )

여기서 median값을 봅시다. median값은 **robustness**한 성질을 가지고 있습니다. 

robustness란 만약 데이터가 어느 방향으로 움직이거나 새로운 데이터가 추가 되었을시 

통계값이 변하지 않으려는 경향을 이야기합니다.

==평소에는 mean을 사용하고 만약, outlier나 skewed distribution이 있을 경우 median을 사용하면 됩니다.

* Spread - variance, sample variance,  diviations, IQR(interquartile range, robustness)

여기서 sample variance는 항상 non-negative이기 때문에 original 데이터와는 성질을 보일수도 있습니다.

예를 들어, 온도 데이터라고 해봅시다. 이때 variance의 unit은 squared 되어버립니다.  
예를 들어, km^2이라는는 데이터가 있을때 variance의 unit은 지수가 4가 되어 버립니다.

그래서 필요한것이 standard deviation입니다. 

*  Skewness and kurtosis

여기서 e = an estimate of skewness,  u = an estimate of kurtosis라고 한다면








### Reference 
* 
* 




> 용어정리 sampling distribution, median(robustness), 


