원문: [An introduction to seaborn](https://seaborn.pydata.org/tutorial/introduction.html)

# 씨본 소개

씨본(seaborn)은 파이썬(Python)에서 통계 그래픽(statistical graphic)을 만들기 위한 라이브러리(library)입니다. 씨본은 [맷플롯립(matplotlib)](https://matplotlib.org/) 위에 구축되었고, [판다스(pandas)](https://pandas.pydata.org/) 자료 구조(data structures)와 밀접하게 통합되어 있습니다.

씨본은 여러분이 데이터를 탐색하고 이해하는 것을 도와줍니다. 씨본의 플로팅 함수(plotting functions)는 전체 데이터셋(dataset)을 담고 있는 데이터프레임(dataframes)과 배열(arrays) 위에서 작동하며, 유익한 플롯(plots)을 만들어내기 위해 필요한 의미론적 매핑(semantic mapping)과 통계 집계(statistical aggregation)를 내부적으로 수행합니다. 씨본의 데이터셋 중심의, 선언적인 API(declarative API)는 여러분이 플롯을 그리는 법에 대한 세부 사항보다는, 플롯의 다양한 구성요소가 의미하는 바에 집중하도록 해줍니다.

여기 씨본이 할 수 있는 것에 대한 예제가 있습니다:

```python
# 씨본을 불러옵니다
import seaborn as sns

# 기본 테마를 적용합니다
sns.set_theme()

# 예제 데이터셋을 불러옵니다
tips = sns.load_dataset("tips")

# 시각화를 생성합니다
sns.relplot(
    data=tips,
    x="total_bill", y="tip", col="time",
    hue="smoker", style="smoker", size="size",
)
```

![](https://seaborn.pydata.org/_images/introduction_1_0.png)

여기에 몇 가지 일이 일어났습니다. 하나씩 살펴봅시다:

```python
# 씨본을 불러옵니다
import seaborn as sns
```

씨본은 우리가 이 간단한 예제를 위해 불러와야 하는 유일한 라이브러리입니다. 관습적으로, `sns`라는 줄임말로 불러옵니다.

무대 뒤편에서, 씨본은 플롯을 그리기 위해 맷플롯립(matplotlib)을 사용합니다. 대화형(interactive) 작업을 위해, 주피터/아이파이썬 인터페이스(Jupyter/IPython interface)를 [맷플롯립 모드](https://ipython.readthedocs.io/en/stable/interactive/plotting.html)로 사용하는 것을 추천드리며, 아니라면 플롯을 보고 싶을 때 [`matplotlib.pyplot.show()`](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.show.html#matplotlib.pyplot.show)를 호출하셔야 할 것입니다.

```python
# 기본 테마를 적용합니다
sns.set_theme()
```

여기서는 맷플롯립 rcParam 시스템을 사용하며, 씨본으로 만들지 않더라도 모든 맷플롯립 플롯이 어떻게 보일지에 영향을 줄 것입니다. 기본 테마 너머에 여러 다른 옵션이 있으며, 여러분은 표현의 맥락에 따라 (예를 들어, 대화 중간에 보여주며 읽을만한 글꼴의 피겨(figure) 버전을 만들 때처럼) 작업을 빠르게 번역해주기 위해 플롯의 스타일과 크기를 독립적으로 조절할 수 있습니다. 맷플롯립 기본값이나 다른 테마를 선호하시면, 이 단계를 건너뛰고 씨본 플로팅 함수를 계속 사용하실 수 있습니다.

```python
# 예제 데이터셋을 불러옵니다
tips = sns.load_dataset("tips")
```

문서 대부분의 코드는 [`load_dataset()`](https://seaborn.pydata.org/generated/seaborn.load_dataset.html#seaborn.load_dataset) 함수를 예제 데이터셋에 빠르게 접근하기 위해 사용합니다. 이 데이터셋들에 특별한 건 없습니다: 그냥 판다스 데이터프레임이고, [`pandas.read_csv()`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.read_csv.html#pandas.read_csv)로 불러왔거나 손으로 만들었어도 됩니다. 문서 대부분의 예제는 판다스 데이터프레임을 사용한 데이터를 지정할 것이지만, 씨본은 받아들이는 [자료 구조](https://seaborn.pydata.org/tutorial/data_structure.html)에 매우 유연합니다.

```python
# 시각화를 생성합니다
sns.relplot(
    data=tips,
    x="total_bill", y="tip", col="time",
    hue="smoker", style="smoker", size="size",
)
```

이 플롯은 tips(팁) 데이터셋의 다섯 개 변수 사이의 관계를 씨본 함수 [`relplot()`](https://seaborn.pydata.org/generated/seaborn.relplot.html#seaborn.relplot)을 한 번 호출하기만 해서 보여줍니다. 우리가 어떻게 변수의 이름만으로 플롯에서 그들의 역할을 제공하는지 주목하세요. 직접 맷플롯립을 사용하는 것과 다르게, 색상 값이나 마커 코드(marker codes)에 대해 플롯 구성요소의 속성(attributes)을 지정해줄 필요가 없었습니다. 무대 뒤편에서, 씨본은 데이터프레임 값에서 맷플롯립이 이해하는 인자(arguments)로의 번역을 처리했습니다. 이 선언적인 접근법은 여러분이 어떻게 맷플롯립을 제어할지에 대한 세부 사항보다는, 대답하고자 하는 질문에 집중할 수 있도록 해줍니다.

## 통계 그래픽을 위한 고수준 API

### 통계 추정

### 분포 표현

### 범주형 데이터 플롯

## 복잡한 데이터셋의 다변량 시각

### 피겨 구축을 위한 저수준 도구

## 완고한 기본값과 유연한 사용자 정의

### 맷플롯립과의 관계

### 다음 단계