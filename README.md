# SAPUI5_Terms

# Fiori UI5 Memory Binding Reference

**제목**: Fiori UI5 Memory Binding Reference

**섹션 1: 메모리 바인딩 관련 주요 메서드 및 용어**

| 구분 | 이름                  | 종류  | 역할 / 설명                            | 예시 코드                                                         |
| -- | ------------------- | --- | ---------------------------------- | ------------------------------------------------------------- |
| 1  | setModel()          | 메서드 | 모델 데이터를 뷰나 전체 앱에 등록                | `this.getView().setModel(oModel);`                            |
| 2  | getModel()          | 메서드 | 등록된 모델 객체를 가져옴                     | `const oModel = this.getView().getModel();`                   |
| 3  | bindElement()       | 메서드 | 특정 경로(Path)에 있는 하나의 객체를 뷰에 바인딩     | `this.getView().bindElement("/EmployeeSet('1001')");`         |
| 4  | bindAggregation()   | 메서드 | 리스트나 테이블처럼 여러 항목을 집합(List) 형태로 바인딩 | `oTable.bindAggregation("items", "/EmployeeSet", oTemplate);` |
| 5  | getBinding()        | 메서드 | 현재 컨트롤에 걸린 바인딩 객체 반환               | `const oBind = oTable.getBinding("items");`                   |
| 6  | getBindingContext() | 메서드 | 특정 컨트롤의 데이터 컨텍스트(바인딩 경로) 가져옴       | `const ctx = oEvent.getSource().getBindingContext();`         |
| 7  | getObject()         | 메서드 | 해당 바인딩 경로의 실제 데이터 객체 반환            | `const obj = ctx.getObject();`                                |
| 8  | getProperty()       | 메서드 | 모델 내 특정 경로의 속성값 가져옴                | `oModel.getProperty("/EmployeeSet/0/Name");`                  |
| 9  | setProperty()       | 메서드 | 모델 내 특정 경로의 값을 변경                  | `oModel.setProperty("/EmployeeSet/0/Name", "홍길동");`           |
| 10 | getValue()          | 메서드 | Input 컨트롤의 사용자 입력값 가져옴             | `const val = this.byId("inpName").getValue();`                |
| 11 | getSelectedKey()    | 메서드 | ComboBox 등에서 선택된 key값 반환           | `const key = this.byId("comboYear").getSelectedKey();`        |
| 12 | getSource()         | 메서드 | 이벤트 발생 컨트롤(버튼 등) 가져옴               | `const src = oEvent.getSource();`                             |
| 13 | updateBindings()    | 메서드 | 모델 데이터 변경 후 UI 갱신                  | `oModel.updateBindings(true);`                                |
| 14 | refresh()           | 메서드 | 서버 데이터 새로고침                        | `oModel.refresh();`                                           |

---

**섹션 2: 바인딩 방식 요약**

| 바인딩 방식              | 의미              | 예시                                      |
| ------------------- | --------------- | --------------------------------------- |
| Property Binding    | 단일 속성 바인딩       | `<Input value="{Name}" />`              |
| Element Binding     | 특정 객체(행) 단위 바인딩 | `bindElement("/Employees('E001')")`     |
| Aggregation Binding | 여러 객체(리스트) 바인딩  | `<List items="{/Employees}">...</List>` |

>[!NOTE]
> - Property Binding : 모델을 UI컨트롤의 프로퍼티에 연결하는 것
> - Aggregation Binding : 모델 데이터에 따라 자식 컨트롤을 자동으로 생성하는 것
> - Element Binding : UI 컨트롤과 바인딩하는 것 (컨트롤을 모델의 특정 항목(데이터 경로) 에 연결하는 것)
> 덕분에 해당 데이터의 속성들을 하위 컨트롤에서도 쉽게 사용할 수 있다.
> ```<Panel headerText="Company Details" binding="{/company}">```
---

* `bindElement()` → 한 객체 단위 바인딩
* `bindAggregation()` → 여러 객체 단위 바인딩
* `getBindingContext()` + `getObject()` → 선택된 항목의 실제 데이터 접근
* `getValue()`, `getSelectedKey()` → 사용자 입력/선택값 취득
* `setProperty()` / `getProperty()` → 모델 데이터 수정/조회

---


## Table vs Panel 바인딩 

- 테이블과 패널의 바인딩 구조가 다르기 때문에 사용하는 방식이 다름


| 컨트롤 종류                 | 바인딩 방식      | 사용하는 메서드                                       | 바인딩 대상       | 결과                   |
| ---------------------- | ----------- | ---------------------------------------------- | ------------ | -------------------- |
| **Table / List**       | 다수 데이터(컬렉션) | `bindItems()` → `getBinding("items").filter()` | 여러 개의 아이템(행) | 여러 행이 반복 렌더링됨        |
| **Panel / SimpleForm** | 단일 데이터(객체)  | `bindElement()`                                | 하나의 객체       | 여러 필드가 한 객체의 속성 값 표시 |


>[!IMPORTANT]
>Table은 내부적으로 items Aggregation을 갖고 있음. 즉, 여러 개의 데이터를 목록으로 렌더링하는 구조이다. (filter 적용가능)
>Panel은 리스트가 아니라 하나의 데이터 객체를 표현하는 컨테이너이다. 즉, items가 아니라 content aggregation을 사용한다. (filter는 배열 데이터를 대상으로 하기 때문에 panel엔 사용이 불가하고, 대신 sPath를 지정한 뒤 bindElement()로 특정 데이터 객체를 직접 연결한다.





esClassInfoSet은 키값이 존재 => TEANO  (pou 03 수정필요)






