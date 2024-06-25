### `Ctrl + O`

extends한 클래스의 메소드를 자동으로 생성해준다.

### `Shift + Shift`

편리한 검색(코드, 파일명 모두 검색 가능하다)

<img src=https://github.com/muyaaho/spring-mvc1/assets/76798969/e0ffe6dc-8ad8-422e-92ac-f32625698350 width="60%" height="60%"/><br>

### `Ctrl + Alt + Shift + T` → `Extract Method...` 선택

함수를 자동으로 분리해준다.

### `Ctrl + Shift + T`
테스트 코드 생성

### `Ctrl + E`
최근 이동한 파일 확인

<img src=https://github.com/muyaaho/spring-mvc1/assets/76798969/c4130e60-7253-46da-9272-b67774da98f4 width="50%" height="50%"/><br>

바로 엔터키 누르면 바로 직전에 있었던 파일로 이동할 수 있다.

### `Ctrl + Alt + N`
Inline
```java
    @Override
    public MyView process(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        MyView myView = new MyView("/WEB-INF/views/new-form.jsp");
        return myView;
    }
```
```java
    @Override
    public MyView process(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        return new MyView("/WEB-INF/views/new-form.jsp");
    }
```
---
https://www.jetbrains.com/help/idea/reference-keymap-win-default.html
