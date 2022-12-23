원문: [An introduction to seaborn](https://seaborn.pydata.org/tutorial/introduction.html)

# 씨본 소개

씨본(seaborn)은 파이썬(Python)에서 통계 그래픽(statistical graphic)을 만들기 위한 라이브러리(library)입니다. 씨본은 [맷플롯립(matplotlib)](https://matplotlib.org/) 위에 구축되었고, [판다스(pandas)](https://pandas.pydata.org/) 자료 구조(data structures)와 밀접하게 통합되어 있습니다.

씨본은 여러분이 데이터를 탐색하고 이해하는 것을 도와줍니다. 씨본의 플로팅 함수(plotting functions)는 전체 데이터셋(dataset)을 담고 있는 데이터프레임(dataframes)과 배열(arrays) 위에서 작동하며, 유익한 플롯(plots)을 만들어내기 위해 필요한 시맨틱 매핑(semantic mapping)과 통계 집계(statistical aggregation)를 내부적으로 수행합니다. 씨본의 데이터셋 중심의, 선언적인 API(declarative API)는 여러분이 플롯을 그리는 법에 대한 세부 사항보다는, 플롯의 다양한 구성요소가 의미하는 바에 집중하도록 해줍니다.

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

데이터를 시각화하기 위해 보편적으로 최고의 방법은 없습니다. 다른 질문은 다른 플롯으로 가장 잘 대답할 수 있습니다. 씨본은 일관적인 데이터셋 지향 API를 이용해 다른 시각 표현 사이를 쉽게 전환할 수 있게 해줍니다.

함수 [`relplot()`](https://seaborn.pydata.org/generated/seaborn.relplot.html#seaborn.relplot)은 많은 여러 통계적 *관계(relationships)*를 시각화하도록 설계되었기 때문에 그렇게 이름지어졌습니다. 산점도(scatter plot)가 종종 효과적이더라도, 한 변수가 시간의 척도를 나타낸다면 관계는 선으로 더 잘 표현됩니다. [`relplot()`](https://seaborn.pydata.org/generated/seaborn.relplot.html#seaborn.relplot) 함수는 여러분이 쉽게 대체 표현으로 전환할 수 있도록 해주는 편리한 `kind` 매개변수(parameter)를 가지고 있습니다:

```python
dots = sns.load_dataset("dots")
sns.relplot(
    data=dots, kind="line",
    x="time", y="firing_rate", col="align",
    hue="choice", size="coherence", style="choice",
    facet_kws=dict(sharex=False),
)
```

![](https://seaborn.pydata.org/_images/introduction_11_0.png)

어떻게 `size`와 `style` 매개변수가 산점도와 선 그래프(line plot)에서 사용되는지 주목하세요, 하지만 이들은 두 시각화에 다른 영향을 미칩니다: 산점도의 마커(marker) 영역과 기호(symbol) 대 선 그래프의 선 굵기와 점표(dashing). 우리는 이것들을 자세하게 생각해둘 필요가 없었단 점은, 플롯의 전체 구조와 우리가 전달하고자 하는 정보에 집중하게 해준다는 것입니다.

### 통계 추정

종종, 우리는 한 변수의 *평균(average)*값을 다른 변수의 함수로 보는 것에 관심이 있습니다. 많은 씨본 함수들이 이러한 질문들에 대답하는 데 필요한 통계 추정(statistical estimation)을 자동적으로 수행해줄 것입니다:

```python
fmri = sns.load_dataset("fmri")
sns.relplot(
    data=fmri, kind="line",
    x="timepoint", y="signal", col="region",
    hue="event", style="event",
)
```

![](https://seaborn.pydata.org/_images/introduction_13_0.png)

통계값이 추정될 때, 씨본은 신뢰 구간(confidence intervals)을 계산하기 위해 부트스트랩(bootstrapping)을 사용하고, 추정의 불확실성을 표현하는 오차 막대(error bars)를 그릴 것입니다.

씨본의 통계 추정은 기술 통계(descriptive statistics)를 넘어섭니다. 예를 들어, [`lmplot()`](https://seaborn.pydata.org/generated/seaborn.lmplot.html#seaborn.lmplot)을 사용해 선형 회귀(linear regression) 모델(과 그 불확실성)을 포함하여 산점도를 향상시킬 수 있습니다:

```python
sns.lmplot(data=tips, x="total_bill", y="tip", col="time", hue="smoker")
```

![](https://seaborn.pydata.org/_images/introduction_15_0.png)

### 분포 표현

통계 분석은 여러분 데이터셋의 변수들의 분포(distribution)에 대한 지식을 필요로 합니다. 씨본 함수 [`displot()`](https://seaborn.pydata.org/generated/seaborn.displot.html#seaborn.displot)은 분포를 시각화하기 위한 다양한 접근법을 지원합니다. 이는 히스토그램(histograms)처럼 고전적인 기법이나 커널 밀도 추정(kernel density estimation)처럼 계산 집약적인(computationally-intensive) 접근법을 포함합니다:

```python
sns.displot(data=tips, x="total_bill", col="time", kde=True)
```

![](https://seaborn.pydata.org/_images/introduction_17_0.png)

또한 씨본은 데이터의 경험적 누적 분포 함수(empirical cumulative distribution function)의 계산과 플로팅처럼, 강력하지만 덜 친숙한 기법을 홍보하려고 시도합니다:

```python
sns.displot(data=tips, kind="ecdf", x="total_bill", col="time", hue="smoker", rug=True)
```

![](https://seaborn.pydata.org/_images/introduction_19_0.png)

### 범주형 데이터 플롯

씨본의 여러 특별한 플롯 유형은 범주형(categorical) 데이터를 시각화하는 데에 중점을 둡니다. 그들은 [`catplot()`](https://seaborn.pydata.org/generated/seaborn.catplot.html#seaborn.catplot)을 통해 접근할 수 있습니다. 이 플롯은 여러 수준의 자세한 정도를 제공합니다. 가장 자세한 수준에서, 여러분은 "군집(swarm)" 플롯을 그려서 모든 관측값을 보기를 희망할 것입니다: 군집 플롯은 범주 축을 따라서 점들의 위치를 조정해 겹치지 않도록 한 산점도입니다:

```python
sns.catplot(data=tips, kind="swarm", x="day", y="total_bill", hue="smoker")
```

![](https://seaborn.pydata.org/_images/introduction_21_0.png)

혹은, 점들이 샘플링되는 기본 분포(underlying distribution)를 표현하기 위해 커널 밀도 추정을 사용하실 수도 있습니다:

```python
sns.catplot(data=tips, kind="violin", x="day", y="total_bill", hue="smoker", split=True)
```

![](https://seaborn.pydata.org/_images/introduction_23_0.png)

또는 중첩된 범주 내에서 평균값과 신뢰 구간만 보여주실 수도 있습니다:

```python
sns.catplot(data=tips, kind="bar", x="day", y="total_bill", hue="smoker")
```

![](https://seaborn.pydata.org/_images/introduction_25_0.png)

## 복잡한 데이터셋의 다변량 관점

일부 씨본 함수는 데이터셋의 유익한 요약들을 빠르게 제공하기 위해 여러 종류의 플롯을 결합합니다. 하나는, [`jointplot()`](https://seaborn.pydata.org/generated/seaborn.jointplot.html#seaborn.jointplot)로, 단일 관계에 초점을 맞춥니다. 이는 각 변수의 주변 분포(marginal distribution)와 함께 두 변수의 결합 분포(joint distribution)를 플로팅합니다.

```python
penguins = sns.load_dataset("penguins")
sns.jointplot(data=penguins, x="flipper_length_mm", y="bill_length_mm", hue="species")
```

![](https://seaborn.pydata.org/_images/introduction_27_0.png)

다른 하나는, [`pairplot()`](https://seaborn.pydata.org/generated/seaborn.pairplot.html#seaborn.pairplot)로, 더 넓은 관점을 취합니다: 이는 각 변수의 모든 쌍별 관계에 대한 결합과 주변 분포를 각각 보여줍니다:

```python
sns.pairplot(data=penguins, hue="species")
```

![](https://seaborn.pydata.org/_images/introduction_29_0.png)

### 피겨 구축을 위한 저수준 도구

이 도구들은 [축 수준(axes-level)](https://seaborn.pydata.org/tutorial/function_overview.html) 플로팅 함수를 피겨의 배열을 관리하는 객체와 결합하여, 데이터셋의 구조를 [축의 격자(grid of axes)](https://seaborn.pydata.org/tutorial/axis_grids.html)에 연결하면서 작동합니다. 두 요소 모두 공개(public) API의 일부로, 여러분은 코드 몇 줄 더 만으로 복잡한 피겨를 만들게끔 직접 사용하실 수 있습니다.

```python
g = sns.PairGrid(penguins, hue="species", corner=True)
g.map_lower(sns.kdeplot, hue=None, levels=5, color=".2")
g.map_lower(sns.scatterplot, marker="+")
g.map_diag(sns.histplot, element="step", linewidth=0, kde=True)
g.add_legend(frameon=True)
g.legend.set_bbox_to_anchor((.61, .6))
```

![](https://seaborn.pydata.org/_images/introduction_31_0.png)

## 완고한 기본값과 유연한 사용자 정의

씨본은 단일 함수 호출로 완전한 그래픽을 만듭니다: 가능하다면, 함수가 플롯의 시맨틱 매핑을 설명하는 유익한 축 레이블(labels)와 범례(legends)를 자동으로 추가할 것입니다.

많은 경우에, 씨본은 데이터의 특성에 기반해 매개변수 기본값도 고를 것입니다. 예를 들어, 지금까지 살펴본 [색상 매핑](https://seaborn.pydata.org/tutorial/color_palettes.html)은 `hue`에 할당한 범주형 변수들의 여러 수준을 표현하기 위해 뚜렷한 색조들(파랑, 주황, 때로는 초록)을 사용했습니다. 수치형 변수를 매핑할 때, 어떤 함수들은 연속적인 기울기로 바뀔 것입니다:

```python
sns.relplot(
    data=penguins,
    x="bill_length_mm", y="bill_depth_mm", hue="body_mass_g"
)
```

![](https://seaborn.pydata.org/_images/introduction_33_0.png)

여러분이 작업을 공유하거나 발표할 준비가 되어있다면, 아마도 기본값으로 이루는 것 이상으로 피겨를 다듬고 싶으실 것입니다. 씨본은 여러 수준의 사용자 정의를 허용합니다. 사용자 정의는 모든 피겨에 적용할 여러 내장 [테마](https://seaborn.pydata.org/tutorial/aesthetics.html)를 정하고, 그 함수는 각 플롯의 시맨틱 매핑을 수정할 수 있는 표준화된 매개변수를 가지며, 추가적인 키워드 인자(keyword arguments)가 아래의 맷플롯립 예술가들에게 전달되어, 훨씬 더 많은 제어를 하게끔 해줍니다. 한 번 플롯을 만드셨다면, 그 속성의 미세 조정을 위해 씨본 API와 맷플롯립 레이어(layer)로 내려가는 방식 모두로 수정을 하실 수 있습니다.

```python
sns.set_theme(style="ticks", font_scale=1.25)
g = sns.relplot(
    data=penguins,
    x="bill_length_mm", y="bill_depth_mm", hue="body_mass_g",
    palette="crest", marker="x", s=100,
)
g.set_axis_labels("Bill length (mm)", "Bill depth (mm)", labelpad=10)
g.legend.set_title("Body mass (g)")
g.figure.set_size_inches(6.5, 4.5)
g.ax.margins(.15)
g.despine(trim=True)
```

![](https://seaborn.pydata.org/_images/introduction_35_0.png)

### 맷플롯립과의 관계

씨본과 맷플롯립의 통합은, 노트북(notebooks)에서의 탐색적 분석(exploratory analysis), GUI 애플리케이션(applications)에서의 실시간 상호작용, 그리고 수많은 래스터(raster)와 벡터(vector) 형식의 보관(archival) 출력을 포함하는, 맷플롯립이 지원하는 많은 환경들(environments)을 여러분이 사용할 수 있게끔 해줍니다.

여러분이 씨본 함수만 사용하더라도 생산적일 수 있지만, 그래픽을 완전히 사용자 정의로 하시려면 맷플롯립의 개념과 API의 일부 지식을 필요로 할 것입니다. 씨본의 새로운 사용자들을 위한 학습 곡선(learning curve)의 한 국면은, 특정 사용자 정의를 이루기 위해서 맷플롯립 레이어로 내려가야만 할 때를 아는 것일 겁니다. 반면에, 맷플롯립에서 오신 사용자분들은 많은 지식이 이전된다는 것을 알 수 있을 것입니다.

맷플롯립은 포괄적이고 강력한 API를 가지고 있습니다; 피겨의 거의 모든 속성을 원하는 대로 바꿀 수 있습니다. 씨본의 고수준 인터페이스와 맷플롯립의 깊은 사용자 정의 기능 간의 결합이, 여러분이 빠르게 데이터를 탐색하고 [출판 품질(publication quality)](https://github.com/wagnerlabpapers/Waskom_PNAS_2017)의 최종 제품에 맞출 수 있는 그래픽을 생성하도록 해줄 것입니다.

### 다음 단계

다음에 어디로 갈지에 대한 몇 가지 옵션이 있습니다. 아마도 여러분은 어떻게 [씨본을 설치](../installing)하는지 배우고 싶으실 겁니다. 그게 끝나면, 여러분은 어떤 종류의 그래픽을 씨본이 생성할 수 있는지 더 넓은 감각을 얻기 위해 [예제 갤러리](https://seaborn.pydata.org/examples/index.html)를 돌아보실 수 있습니다. 또는 여러 도구들과, 이 도구들이 설계될 때의 목적에 대한 깊은 논의를 위해서 남은 [사용자 안내와 튜토리얼](../tutorial)을 읽어나가실 수도 있습니다. 생각하고 있는 특정 플롯이 있고 어떻게 만드는지 알고싶으시다면, 각 함수의 매개변수를 문서화하고 사용법을 설명하기 위한 많은 예제를 보여주는, [API 참조](https://seaborn.pydata.org/api.html)를 확인하실 수 있습니다.
