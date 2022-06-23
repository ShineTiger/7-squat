## 목차
- [개요](#개요)
- [기술스택](#기술스택)
- [목표기능](#목표기능)
- [필요공부](#필요공부)
- [고민점](#고민점)

## 개요

5초를 내려가고 2초간 가만히 있는 7초스쿼트. 

올라오는 시간까지 포함해서 10초. 

즉, 10초가 1회, 10회가 1세트, 휴식시간은 30초~1분. 3세트를 하면 완료.

초에 따라 실시간으로 변하는 스쿼트 동작 이미지를 가이드로 삼을 수 있다.

## 기술스택
- react
  - useState, useEffect, useRef
- TS
- Tailwind

## 목표기능

### 스톱워치를 이용한 스쿼트 횟수와 세트 카운팅(스쿼트카운터)

- 스쿼트1회 = 10초 이므로, 초를 세는 카운터를 핵심 카운터를 넣어서 세트를 셀 수 있다.  
- 1초마다 스쿼트를 동작하는 이미지가 변경된다

#### 스톱워치 
1. state에는 초기값으로 0을 넣는다. 
2. 초를세는 메소드인 setInterval()

#### 횟수 카운팅 
1. setInterval()로 초를 센다.
2. useRef를 이용해서 setInterval()로 카운트한 초를 current에 저장한다. 
3. current가 10이 되면 횟수 카운터가 1을 기록한다. 

#### 세트 카운팅 
1. 횟수카운터가 10이 된다면 세트 카운터가 1을 기록한다(100초)
2. 세트카운터가 1이 된다면 바로 휴식시간 타이머가 시작된다.

#### 이미지 가이드 
1. setInterval()을  setState로 두어서 1초간 state가 변경될때마다 새로운 이미지를 렌더링한다.

#### 스쿼트 카운트 종료 
1. 100초가 경과되면 종료된다.

### 휴식 타이머 

- 최대 1분까지이며, 1분을 넘기면 휴식타이머가 종료되고 곧바로 스쿼트카운터가 작동된다. 
- 57초가 되거나 그 이전에 종료버튼을 누르면 3초만 세는 준비타이머가 작동된다.

#### 휴식시작 

#### 휴식종료 

### 준비타이머

- 최초 스쿼트 시작시 작동된다
- 휴식 타이머가 종료되었을 시 작동된다

### 최초시작과 일시정지

### 스쿼트 종료와 조기종료

- 조기종료는 휴식 타이머에서만 가능하다.

### 완료 기록

- 주별, 월별로 열람할 수 있다. 
- 날짜에 따라 조기종료와 종료
- 7초스쿼트를 완료한 날짜가 기록된다. 

## 필요공부
- 상태관리 라이브러리(redux)
- tailwind 적용법
- TS 

## 고민점
- setTimeOut() 메소드를 사용할 것인가? 
- 이미지 가이드에만 useEffect를 사용할 것인가?
