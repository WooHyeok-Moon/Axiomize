---
author: "Woohyeok Moon"
date: 2024-03-14
title: 환경 데이터 종류
categories: 환경 빅데이터 분석 및 통계 추론
tags: [time-series data, spatial data, spatio-temporal data]
showtoc: false
weight: 10
---

# Basics of Environmental Data

## 1) 환경 데이터 특징

### 1.1) 시계열 데이터 (Time-series data)

continous한 시간 간격에 따른 데이터. 시간, 일 또는 월 별 데이터와 같이 규칙적일 수도 있고, interval 자체가 불규칙적일 수도 있다.

예시:
- 계절, 연 단위의 강우량 변화
- 강, 호수, 댐 등의 수위
- 호수나 시냇물의 유량
- pH, 혼탁도, 오염도 등과 같은 수질

시계열 데이터 특성:
- 시간 종속성(Temporal dependency): 일반적인 데이터와 다르게 시계열 데이터는 고려해야 할 X(독립 변수) 시간 경과에 따른 특징이 존재하며, 이를 통해 유용한 정보를 얻을 수 있다. 하지만 이러한 특징이 결측치, 노이즈, 계절성, 추세 및 인과관계 처리와 같은 feature engineering에 어려움을 줄 수도 있다. ([How to handle temporal dependencies in feature engineering](https://www.linkedin.com/advice/1/how-can-you-handle-temporal-dependencies-feature))
- 계절성(Seasonality): 계절에 따른 반복성 또는 주기가 존재한다.
- 추세(Trend): 특정 지역의 지하수가 점진적으로 고갈되는 것과 같이, 시간 경과에 따른 데이터의 **장기적인** 추세가 존재한다.

### 1.2) 공간 데이터(Spatial Data)

지리적, 공간적 정보를 포함한 데이터. 지구상의 특정한 위치에서 일어나는 현상을 표현하고 분석하는 데에 쓰인다.

예시:
- 강, 호수 및 대수층($\approx$지하수층, 'aquifers' in English)
- 각 토지의 쓰임새와 그로 인해 발생하는 주변 수질 또는 수위의 변화
- [^1]infrastructure 건설 시의 기대 효과 분석
- 토지의 침식 및 퇴적

공간 데이터 특성:
- 위치(Location)는 좌표(위도 및 경도) 또는 기타 지리적 척도를 통해 표현된다.
- Attribute(설명변수) 정보는 LULC(Land Use Land Cover)나 수질을 통해 표현한다. (보통 map에 color로 구분)
- 날짜의 경과에 따른 해수면의 변화
- 공간 관계성: 각 지역 간 서로 어떤 관계에 있는지를 나타내는 정보. e.g. 인접(adjacency): 서로 접해있는가, 포함(containment): A 지역이 B 지역을 포함하고 있는가

### 1.3) 시공간 데이터(Spatio-Temporal Data)

시간적, 공간적 정보를 모두 담고 있는 데이터. 시공간에 영향을 받는 환경 현상을 역동적으로 보여준다. 복잡한 환경 현상을 이해하는 데에 유용하다.

예시:
- 계절, 연도별 강수량 패턴. 현재 NASA에서는 [^3]GPM을 수행하고 있다.
- 시간 경과에 따른 토지 사용 방식의 변화
- 시간 경과에 따른 각 유역(watershed)의 수질 변화
- 수온 및 수질 변화에 따른 수상생물의 계절 단위 이동

시공간 데이터 특성:
- Dynamic Location Information: 특정 현상이 시간이 지남에 따라 어디로 이동하는지 역동적으로 파악 가능하다. (focus on phenomenon)
- Temporal Changes: 특정 지역에서 시간이 지남에 따라 어떤 현상이 발생하는지 파악 가능하다. (focus on location)
- Complex Data Structure: 시간과 공간이 모두 포함된 고차원 데이터이기 때문에 정교한 분석 기법이 필요하다.

[^1]: 사회적 생산 기반. 또는, 경제 활동의 기반을 형성하는 기초적인 시설. 댐·도로·항만·발전소·통신 시설 등의 산업 기반 및 학교·병원·공원 등의 사회 복지·환경 시설이 이에 해당함. 인프라.  
[^2]: 어떤 종류의 토지가 어떻게 쓰이는지를 나타내는 지도 = LULC map  
[^3]: GPM(Global Precipitation Measurement Mission): 인공위성을 통해 전 세계의 강수량을 측정하는 mission
