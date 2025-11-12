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

---

**섹션 3: 핵심 포인트**

* `bindElement()` → 한 객체 단위 바인딩
* `bindAggregation()` → 여러 객체 단위 바인딩
* `getBindingContext()` + `getObject()` → 선택된 항목의 실제 데이터 접근
* `getValue()`, `getSelectedKey()` → 사용자 입력/선택값 취득
* `setProperty()` / `getProperty()` → 모델 데이터 수정/조회

---

