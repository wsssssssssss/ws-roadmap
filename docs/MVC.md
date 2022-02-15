# MVC

C 모듈 PHP의 근간을 이루는 디자인패턴인 MVC를 알아보자.
앱을 Model, View, Controller 세가지로 나누는 디자인패턴이다.
앱의 간략한 흐름은 Controller에서 Model의 데이터를 가져오고 가져온 데이터는 View에 넘겨줘서 화면을 그린다.
UI와 비즈니스 로직의 분리가 주요 장점이다. (비즈니스 로직 = Model, UI = View, 그 사이 중간다리 = Controller)

## Model
데이터 처리를 담당한다. php 템플릿 기준으로는 따로 Model이 존재하지 않고 DB만 존재한다.

### 하는일
- DB만 존재하기 때문에 DB에 대한 crud 액션만 제공한다.

## View
UI를 그리는 기능을 담당한다. php 템플릿 기준으로는 view 함수이다.

### 하는일
- view 함수를 통해 화면에 UI를 그린다.

## Controller
Model의 데이터를 업데이트하거나 Model의 데이터를 View에 넘겨준다. php 템플릿 기준으로는 Controller들이다.

### 하는일
- 필요할 경우 DB를 통해 데이터를 가져와서 view 함수를 통해 화면에 UI를 그린다.

## Flow (php template 기준)
1. 유저가 앱에 접근시 Route를 통해서 url에 해당하는 Controller를 가져온다.
2. Controller에서는 데이터가 필요하면 DB를 통해 가져온다.
3. view 함수를 통해 UI를 그려준다.
4. 끗