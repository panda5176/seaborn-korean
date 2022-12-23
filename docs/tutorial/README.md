원문: [User guide and tutorial](https://seaborn.pydata.org/tutorial.html)

# 사용자 안내와 튜토리얼

### [씨본 소개](introduction)

- [통계 그래픽을 위한 고수준 API](introduction#통계-그래픽을-위한-고수준-API)
- [복잡한 데이터셋의 다변량 관점](introduction#복잡한-데이터셋의-다변량-관점)
- [완고한 기본값과 유연한 사용자 정의](introduction#완고한-기본값과-유연한-사용자-정의)

## API 개요

### [씨본 플로팅 함수 개요](function_overview)

- [비슷한 작업을 위한 비슷한 함수](function_overview#비슷한-작업을-위한-비슷한-함수)
- [피겨 수준 함수 대 축 수준 함수](function_overview#피겨-수준-함수-대-축-수준-함수)
- [데이터의 여러 관점을 결합하기](function_overview#데이터의-여러-관점을-결합하기)

### [씨본에서 허용하는 자료 구조](data_structure)

- [긴 형식 데이터 대 넓은 형식 데이터](data_structure#긴-형식-데이터-대-넓은-형식-데이터)
- [긴 형식 데이터를 시각화하기 위한 옵션](data_structure#긴-형식-데이터를-시각화하기-위한-옵션)
- [넓은 형식 데이터를 시각화하기 위한 옵션](data_structure#넓은-형식-데이터를-시각화하기-위한-옵션)

## 객체 인터페이스

### [seaborn.objects 인터페이스](objects_interface)

- [플롯을 지정하고 데이터 매핑하기](objects_interface#플롯을-지정하고-데이터-매핑하기)
- [플로팅 전에 데이터 변환하기](objects_interface#플로팅-전에-데이터-변환하기)
- [플롯 작성하고 표시하기](objects_interface#플롯-작성하고-표시하기)
- [모양을 사용자 지정하기](objects_interface#모양을-사용자-지정하기)

### [Mark 객체의 속성](properties)

- [좌표 속성](properties#좌표-속성)
- [색상 속성](properties#색상-속성)
- [스타일 속성](properties#스타일-속성)
- [크기 속성](properties#크기-속성)
- [텍스트 속성](properties#텍스트-속성)
- [다른 속성](properties#다른-속성)

## 플로팅 함수

### [통계적 관계 시각화하기](relational)

- [산점도로 변수 연관짓기](relational#산점도로-변수-연관짓기)
- [선 그래프로 연속성 강조하기](relational#선-그래프로-연속성-강조하기)
- [패싯으로 다중 관계 보여주기](relational#패싯으로-다중-관계-보여주기)

### [데이터 분포 시각화하기](distributions)

- [단변량 히스토그램 플로팅](distributions#단변량-히스토그램-플로팅)
- [커널 밀도 추정](distributions#커널-밀도-추정)
- [경험적 누적 분포](distributions#경험적-누적-분포)
- [이변량 분포 시각화하기](distributions#이변량-분포-시각화하기)
- [다른 설정에서 분포 시각화](distributions#다른-설정에서-분포-시각화)

### [범주형 데이터 시각화하기](categorical)

- [범주형 산점도](categorical#범주형-산점도)
- [분포 비교하기](categorical#분포-비교하기)
- [중심 경향치 추정하기](categorical#중심-경향치-추정하기)
- [추가 차원 보여주기](categorical#추가-차원-보여주기)

## 통계 작업

### [통계적 추정과 오차 막대](error_bars)

- [데이터 산포 척도](error_bars#데이터-산포-척도)
- [추정 불확실성 척도](error_bars#추정-불확실성-척도)
- [회귀 적합의 오차 막대](error_bars#회귀-적합의-오차-막대)
- [오차 막대로 충분한가요?](error_bars#오차-막대로-충분한가요)

### [회귀 적합 추정하기](regression)

- [선형 회귀 모델을 그리기 위한 함수](regression#선형-회귀-모델을-그리기-위한-함수)
- [여러 종류의 모델 적합하기](regression#여러-종류의-모델-적합하기)
- [다른 변수에 조건화하기](regression#다른-변수에-조건화하기)
- [다른 맥락에서 회귀 플로팅하기](regression#다른-맥락에서-회귀-플로팅하기)

## 다중 플롯 격자

### [구조화된 다중 플롯 격자 짓기](axis_grids)

- [조건적인 스몰 멀티플즈](axis_grids#조건적인-스몰-멀티플즈)
- [사용자 정의 함수 사용하기](axis_grids#사용자-정의-함수-사용하기)
- [쌍별 데이터 관계 플로팅하기](axis_grids#쌍별-데이터-관계-플로팅하기)

## 피겨 미학

### [피겨 미학 조절하기](aesthetics)

- [씨본 피겨 스타일](aesthetics#씨본-피겨-스타일)
- [축 테두리 제거하기](aesthetics#축-테두리-제거하기)
- [일시적으로 피겨 스타일 설정하기](aesthetics#일시적으로-피겨-스타일-설정하기)
- [씨본 스타일 요소 덮어쓰기](aesthetics#씨본-스타일-요소-덮어쓰기)
- [플롯 요소 스케일링](aesthetics#플롯-요소-스케일링)

### [색상 팔레트 고르기](color_palettes)

- [플롯에서 색상을 사용하는 일반 원칙](color_palettes#플롯에서-색상을-사용하는-일반-원칙)
- [컬러 팔레트를 고르는 도구](color_palettes#컬러-팔레트를-고르는-도구)
- [질적 컬러 팔레트](color_palettes#질적-컬러-팔레트)
- [순차적 컬러 팔레트](color_palettes#순차적-컬러-팔레트)
- [다양한 컬러 팔레트](color_palettes#다양한-컬러-팔레트)
