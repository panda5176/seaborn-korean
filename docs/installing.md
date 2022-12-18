원문: [Installing and getting started](https://seaborn.pydata.org/installing.html)

# 설치하고 시작하기

시본(seaborn)의 공식 릴리즈(releases)는 PyPI에서 설치할 수 있습니다:

```sh
pip install seaborn
```

`pip`의 기본 호출은 시본과, 필요하다면 필수적인 의존 항목들(dependencies)을 설치할 것입니다. 몇 가지 고급 기능에 접근할 수 있도록 선택적인 의존 항목들을 포함할 수 있습니다.

```sh
pip install seaborn[stats]
```

라이브러리(library)는 [아나콘다(Anaconda)](https://repo.anaconda.com/) 배포(distribution)의 일부로도 포함되어있으며, `conda`와 같이 설치할 수 있습니다:

```sh
conda install seaborn
```

메인(main) 아나콘다 저장소(repository)는 새로운 릴리즈를 추가하기에는 느릴 수도 있으므로, 여러분이 [콘다포지(conda-forge)](https://conda-forge.org/) 채널을 사용하는 걸 선호할 수도 있습니다.

```sh
conda install seaborn -c conda-forge
```

## 의존 항목들

### 지원되는 파이썬 버전

- 파이썬 3.7+

### 필수적인 의존 항목들

- [넘파이(numpy)](https://numpy.org/)
- [판다스(pandas)](https://pandas.pydata.org/)
- [맷플롯립(matplotlib)](https://matplotlib.org/)

### 선택적인 의존 항목들

- [스탯츠모델즈(statsmodels)](https://www.statsmodels.org/), 고급 회귀(regression) 도표를 위해
- [사이파이(scipy)](https://www.scipy.org/), 군집화 행렬(clustering matrices)과 몇몇 고급 옵션을 위해
- [패스트클러스터(fastcluster)](https://pypi.org/project/fastcluster/), 거대한 행렬의 빠른 군집화

## 빠른 시작

시본을 설치하시면, 시작할 준비가 되신겁니다. 테스트해보기 위해, 예제 데이터셋(dataset) 중 하나를 불러와서 도표화(plot)할 수 있습니다:

```python
import seaborn as sns
df = sns.load_dataset("penguins")
sns.pairplot(df, hue="species")
```

[맷플롯립 모드(matplotlib mode)](https://ipython.readthedocs.io/en/stable/interactive/plotting.html)가 활성화된 주피터 노트북(Jupyter notebook)이나 아이파이썬 터미널(IPython terminal)에서 작업하고 계시다면, 바로 도표를 보실 수 있을겁니다. 아니라면, 명시적으로 [`matplotlib.pyplot.show()`](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.show.html#matplotlib.pyplot.show)를 호출하셔야 할겁니다.

```python
import matplotlib.pyplot as plt
plt.show()
```

시본만 불러와도(imported) 꽤나 멀리 갈 수 있지만, 맷플롯립 함수(functions)에 접근하는 것이 가끔 유용합니다. 튜토리얼과 API 문서는 보통 다음 불러오기를 가정합니다:

```python
import numpy as np
import pandas as pd

import matplotlib as mpl
import matplotlib.pyplot as plt

import seaborn as sns
import seaborn.objects as so
```

## 설치 문제 디버깅

시본 코드 기반(codebase)은 순수한 파이썬(Python)이며, 라이브러리는 문제 없이 보통 설치되어야 합니다. 때때로, 의존 사항들이 컴파일된(compiled) 코드와 시스템 라이브러리(system libraries)에 링크(link)를 포함하기 때문에 어려움이 발생할 것입니다. 이러한 어려움은 보통 불러오기에서 `"DLL load failed"` 같은 메시지와 함께 오류로 나타납니다. 이러한 문제를 디버그(debug)하려면, 어떤 특정 라이브러리가 불러오기에 실패했는지 파악하기 위한 예외 추적(exception trace)을 정독하고, 여러분의 특정 시스템을 위한 팁을 가지고 있는지 보기 위해 그 패키지의 설치 문서를 확인하세요.

어떤 경우에는, 시본의 설치가 성공한 것처럼 보이지만, 불러오기를 시도하면 `"No module named seaborn"`이라는 메시지와 함께 오류가 발생할 수 있습니다. 이건 보통 여러분이 시스템에 여러 파이썬 설치본을 가지고 계시고 `pip`나 `conda`가 여러분 인터프리터(interpreter)가 살아있는 곳과 다른 설치본을 가리키고 있을 때를 의미합니다. 이 문제를 해결하는 것은 여러분 시스템의 경로를 정렬해야 하지만, 가끔 `pip`를 `python -m pip install seaborn`과 같이 호출하면 무시되기도 합니다.

## 도움 받기

시본에서 버그와 마주쳤다고 생각하시면, [깃헙 이슈 트래커(GitHub issue tracker)](https://github.com/mwaskom/seaborn/issues)에 제보해주세요. 유용해지려면, 버그 제보는 다음의 정보를 포함해야 합니다:

- 문제를 묘사하는 재현 가능한 코드 예시
- 보고 있는 출력(도표 이미지나 에러 메시지)
- 무언가 잘못되었다고 생각하는 이유에 대한 명확한 설명
- 작업 중인 시본과 맷플롯립의 특정 버전

버그 제보는 시본 문서의 예시 데이터셋 중 하나를 사용해 (예를 들어 `load_dataset()`과 함께) 묘사할 수 있다면 처리하기 가장 쉽습니다. 그렇지 않다면, 예제가 문제를 재현하기 위한 합성(synthetic) 데이터를 생성하면 좋습니다. 여러분의 실제 데이터셋으로만 문제를 묘사할 수 있다면, 이상적으로는 csv로, 데이터셋을 공유하셔야 할 것입니다.

오류와 마주치셨다면, 새로운 이슈(issue)를 열기 전에 메시지의 특정 텍스트(text)를 검색하면 문제를 빠르게 해결하고 중복 보고를 만드는 걸 피하는데 자주 도움이 될 것입니다.

맷플롯립이 실제 렌더링(rendering)을 다루기 때문에, 오류나 정확하지 않은 출력이 시본보다는 맷플롯립의 문제 때문일 수 있습니다. 여러분이 맷플롯립만 사용하는 예제로 문제를 재현한다면, 올바른 위치에 문제를 제보할 수 있어 시간을 아낄 수 있습니다. 하지만 방법이 명확하지 않다면 이 단계를 건너뛰어도 괜찮습니다.

일반적인 지원 질문은, 여러분의 게시물을 보고 적절한 도움을 제공할 수 있는 많은 사람들이 있는 [스택오버플로우(stackoverflow)](https://stackoverflow.com/questions/tagged/seaborn/)가 더 편합니다. [실행할 수 있는 코드](https://stackoverflow.com/help/minimal-reproducible-example), 얻고자 하는 것이 정확한 구문, 그리고 마주친 문제에 대한 정확한 설명을 포함하시면 빠른 답변을 얻으실 수 있는 가능성이 높아집니다.
