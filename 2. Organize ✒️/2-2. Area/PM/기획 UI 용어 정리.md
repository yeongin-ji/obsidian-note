>(1) 날짜: 2024.03.31
>(2) 태그(주제/카테고리): #PM #UX/UI #용어명세 

>(3) Link
- [[Project Manager]]
---

### BTN 상태(State) 정리
![[Pasted image 20240331135141.png]]

- Enabled: 상호작용이 가능한 상태
- Disabled: (어떤 이유로든) 동작할 수 없는 비활성 상태
- Hover: 마우스 또는 포인터가 올려진 상태
- Focused: 키보드 또는 음성 등의 입력을 통해 강조된 상태
- Pressed: 마우스 또는 포인터로 클릭/터치했을 때 

### GNB (Global Navigation Bar)
![[Pasted image 20240331135601.png]]

### LNB (Local Navigation Bar)
![[Pasted image 20240331135649.png]]

### Main Banner (Hero Banner)
![[Pasted image 20240331135739.png]]

### Drop Down List (Pulldown Menu)
![[Pasted image 20240331135858.png]]

### Modal / Popup
![[Pasted image 20240331140019.png]]

- **Modal**은 기존에 열려있던 페이지 위에 새로운 레이어를 덮는 개념
- **Popup**은 페이지 위에 또 하나의 페이지를 띄우는 개념
- 팝업이 차단되는 경우를 대비해 중요한 정보는 Modal을 통해 전달하는 것이 좋다.

### Snack Bar / Toggle / Tooltip
![[Pasted image 20240331140251.png]]

- **Snack Bar**는 유저가 수행한 작업에 대한 결과(피드백)를 간단한 텍스트 레이블 형태로 보여준다. 4초 뒤 화면에서 사라지며, 액션 버튼이 함께 표시된다는 점에서 토스트 메시지와는 차이가 있다.
- **Toggle**, Switch라고도 하며 설정 켜기/끄기와 같은 항목에 적용할 수 있다.
- **Tooltip**은 특정 요소에 마우스를 가져가면(Hovering) 나타나는 설명이다. 부연 설명을 표시할 때유용하다.

### Input Field
![[Pasted image 20240331142552.png]]

- **Input Field**는 사용자가 텍스트를 입력하고 편집할 수 있는 입력란을 의미한다.
- **유효성 검사**는 유저가 필수 입력 요소를 생략했거나, 정해진 양식에 맞춰 입력하지 않았을 경우오류 상태를 표시하여 양식에 맞는 데이터 입력을 유도한다.
- 여러 줄 입력을 필요로 할 때는 **Textarea**를 주로 사용한다.

### Check Box
![[Pasted image 20240331142846.png]]

- **Check Box**는 다중 선택에 사용되는 컴포넌트로, 하나의 요소만 선택 가능한 **Radio Button**과는 차이가 있다.

### Accordion
![[Pasted image 20240331143051.png]]

### Bread Crumb (브레드 크럼)
![[Pasted image 20240331143134.png]]

- *PC 웹 환경에서 자주 활용*되는 정보 구조 기법으로, 빵 부스러기라는 이름처럼 사용자가 지나온 위치를 표함하여, 현재의 위치를 시각적 계층 구조로 나타내는 네비게이션이다.

>(5) Reference
- 