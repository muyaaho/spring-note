## 회원 웹 기능 - 홈 화면 추가

### 홈 컨트롤러 추가

```java
@GetMapping("/")
public String home() {
    return "home";
}
```

- `@GetMapping`
- [localhost:8080](http://localhost:8080) 으로 들어가면 home.html 파일을 보여준다.

## 회원 웹 기능 - 등록

### 회원 등록 폼 개발

```java
@GetMapping("/members/new")
public String createForm() {
    return "members/createMemberForm";
}
```

```html
<form action="/members/new" method="post">
    <div class="form-group">
        <label for="name">이름</label>
        <input type="text" id="name" name="name" placeholder="이름을 입력하세요">
    </div>
    <button type="submit">등록</button>
</form>
```

- `<form>`: 값 입력
    - action url로 post 방식으로 값이 들어온다.
- input 태그의 name 속성은 서버로 들어올 때 key 값이다.

### 회원 등록 컨트롤러

```java
public class MemberForm {
    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

- html의 name 속성과 같은 필드 값을 가진다.
- getter, setter를 모두 선언한다.

```java
@PostMapping("/members/new")
public String create(MemberForm form) {
    Member member = new Member();
    member.setName(form.getName());

    memberService.join(member);

    return "redirect:/";
}
```

- `@PostMapping`으로 url을 설정한다.
- form의 필드가 private이므로 setName을 통해 값을 변경한다.

## 회원 웹 기능 - 조회

```java
@GetMapping("/members")
public String list(Model model) {
    List<Member> members = memberService.findMembers();
    model.addAttribute("members", members);
    return "members/memberList";
}
```

- `findMembers()` 메서드를 통해 멤버 값을 찾아준다.
- addAttribute로 모델에 “members” 속성을 저장한다.

```html
<div class="container">
    <div>
        <table>
            <thead>
            <tr>
                <th>#</th>
                <th>이름</th>
            </tr>
            </thead>
            <tbody>
            <tr th:each="member : ${members}">
                <td th:text="${member.id}"></td>
                <td th:text="${member.name}"></td>
            </tr>
            </tbody>
        </table>
    </div>
</div> <!-- /container -->
```

- `th:each`: for each같이 members의 값을 하나씩 꺼낸다.
