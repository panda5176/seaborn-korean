원문: [Overview of seaborn plotting functions](https://seaborn.pydata.org/tutorial/function_overview.html)

# 씨본 플로팅 함수 개요

씨본(seaborn)과의 상호작용 대부분은 플로팅 함수(plotting functions) 집합을 통해 발생할 것입니다. 튜토리얼의 이 다음 장들에서는 각 함수가 제공하는 특정 기능을 탐색할 것입니다. 이 장에서는 여러분이 마주하실 고수준의, 여러 종류의 함수를 소개할 것입니다.

## 비슷한 작업을 위한 비슷한 함수

씨본 이름공간(namespace)은 평평합니다; 모든 기능은 최상위 수준에서 접근할 수 있습니다. 하지만 코드 자체는, 다른 방법으로 비슷한 시각화 목표를 달성하는 함수들의 모듈(modules)로 계층적으로 구조화되어(hierarchically structured) 있습니다. 대부분의 문서는 이러한 모듈들을 중심으로 구성되어 있습니다: 여러분은 "관계형(relational)", "분포형(distributional)", 그리고 "범주형(categorical)" 같은 이름과 마주치실 것입니다.

예를 들어, [분포형 모듈](https://seaborn.pydata.org/api.html#distribution-api)은 데이터 점(datapoints)의 분포를 표현하는데 특화된 함수들을 정의합니다. 이는 히스토그램(histogram)과 같은 친숙한 메서드(methods)를 포함합니다:

```python
penguins = sns.load_dataset("penguins")
sns.histplot(data=penguins, x="flipper_length_mm", hue="species", multiple="stack")
```

![](https://seaborn.pydata.org/_images/function_overview_3_0.png)

비슷한, 하지만 아마도 덜 익숙한, 커널 밀도 추정(kernel density estimation)과 같은 옵션들:

```python
sns.kdeplot(data=penguins, x="flipper_length_mm", hue="species", multiple="stack")
```

![](https://seaborn.pydata.org/_images/function_overview_5_0.png)

모듈의 함수들은 수많은 아래의 코드들을 공유하고, (위 예제의 `multiple="stack"처럼) 라이브러리(library)의 다른 구성요소들에서는 보이지 않을 유사한 기능들을 제공합니다. 그들은 데이터셋을 탐색할 때 다른 시각 표현(visual representations) 사이 전환을 촉진하도록 설계되었는데, 이는 다른 표현들이 종종 보완적으로 강점과 약점을 갖기 때문입니다.

## 피겨 수준 함수 대 축 수준 함수

여러 모듈뿐 아니라, "축 수준(axes-level)"이나 "피겨 수준(figure-level)" 같은 씨본 함수의 횡단(cross-cutting) 분류도 있습니다. 위의 예제들은 축 수준 함수입니다. 그들은 데이터를 함수의 반환 값(return value)인 단일한 `matplotlib.pyplot.Axes` 객체(object)에 플롯합니다.

대조적으로, 피겨 수준 함수는 주로 [`FacetGrid`](https://seaborn.pydata.org/generated/seaborn.FacetGrid.html#seaborn.FacetGrid)인, 피겨를 관리하는 씨본 객체를 통해 맷플롯립(matplotlib)과 마주합니다. 각 모듈은 다양한 축 수준 함수에 대해 유일한 인터페이스(interface)를 제공하는 단일한 피겨 수준 함수를 가집니다. 구조는 대략 이렇습니다:

![](https://seaborn.pydata.org/_images/function_overview_8_0.png)

예를 들어, [`displot()`](https://seaborn.pydata.org/generated/seaborn.displot.html#seaborn.displot)은 분포 모듈의 피겨 수준 함수입니다. 기본 행동은 화면 뒤에서 [`histplot()`](https://seaborn.pydata.org/generated/seaborn.histplot.html#seaborn.histplot)과 같은 코드를 사용해 히스토그램을 그리는 것입니다:

```python
sns.displot(data=penguins, x="flipper_length_mm", hue="species", multiple="stack")
```

![](https://seaborn.pydata.org/_images/function_overview_10_0.png)

대신 커널 밀도 플롯을 그리려면, `kind` 매개변수(parameter)를 사용해 선택한 [`kdeplot()`](https://seaborn.pydata.org/generated/seaborn.kdeplot.html#seaborn.kdeplot)과 같은 코드를 쓰면 됩니다.

```python
sns.displot(data=penguins, x="flipper_length_mm", hue="species", multiple="stack", kind="kde")
```

![](https://seaborn.pydata.org/_images/function_overview_12_0.png)

## 데이터의 여러 관점을 결합하기
