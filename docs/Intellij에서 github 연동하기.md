1. VCS - Share Project on Github

![image](https://github.com/muyaaho/spring-basic/assets/76798969/abdc2dd6-940f-4938-8284-2ccdb2219683)


1. 레포지토리 이름 설정
    
   ![image](https://github.com/muyaaho/spring-basic/assets/76798969/7ee12c2f-5b00-4634-8a32-85a4e788abfe)

    

이렇게 하면 자동으로 기존에 있던 파일들을 커밋할 수 있다.

![image](https://github.com/muyaaho/spring-basic/assets/76798969/7a97643e-2917-45d0-89d8-667cb6000cb2)


commit 창에서 스테이징, 커밋을 할 수 있다. 커밋 메시지를 잘못 작성했을 때(push 하기 전) Amend를 누르면 쉽게 커밋 메시지를 고칠 수 있다.

![image](https://github.com/muyaaho/spring-basic/assets/76798969/bb29b47f-d619-47b4-8ea1-0c2770df2b9c)


메뉴 창에서 pull(Update Project), Push, 브랜치 관리를 할 수 있다. 

참고로 git bash에서 브랜치를 생성해 체크아웃하면 intellij의 브랜치도 바뀌어 있는 모습을 확인할 수 있다.

![image](https://github.com/muyaaho/spring-basic/assets/76798969/7ad7d99e-7e12-4101-a5ea-f7f7da90c28d)


---

근데 이렇게 커밋을 하면 push와 pull을 하니 에러가 발생하고 마는데...

[Git push가 안되는 경우 (fatal: refusing to merge unrelated histories)](https://gdtbgl93.tistory.com/63)

![image](https://github.com/muyaaho/spring-basic/assets/76798969/4d75f678-1ea8-4b2a-a758-0bb46c6ffb49)


위의 블로그를 따라 git bash에서 pull을 실행했더니 conflict 발생한다.

![image](https://github.com/muyaaho/spring-basic/assets/76798969/c1d83ce0-2970-4d97-84dd-059cb5db9661)



자동을 intellij에 conflict된 파일이 뜨는데, 충돌을 해결한다.

![image](https://github.com/muyaaho/spring-basic/assets/76798969/56b4bd55-3003-4bb6-8f83-63c291a8d31b)


![image](https://github.com/muyaaho/spring-basic/assets/76798969/4491da2f-c0d7-493e-a2fa-2464c068077e)


이제 merge가 되었다.

![image](https://github.com/muyaaho/spring-basic/assets/76798969/d9f8222a-c133-4350-ae0c-2fc08c2ed9b1)

```python
On branch main
Your branch and 'origin/main' have diverged,
and have 7 and 1 different commits each, respectively.
  (use "git pull" to merge the remote branch into yours)

All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

```

일단 pull을 다시 했더니 커밋을 먼저 하라고 해서 커밋 시도 한다. merge된 상태에서 커밋을 안하고 pull을 시도했던 것이었다..

![image](https://github.com/muyaaho/spring-basic/assets/76798969/359ad22c-0dd1-4c67-8842-c5deabebc8e8)


![image](https://github.com/muyaaho/spring-basic/assets/76798969/150a4674-f568-41ce-94ad-6765f891a8d7)


merge를 커밋 하고 다시 pull을 시도하면 merge가 잘 된 모습을 확인할 수 있다.

![image](https://github.com/muyaaho/spring-basic/assets/76798969/1958ef5b-1594-4f22-b0c7-53b1878fe872)


그리고 push하면 잘 되는 모습을 확인할 수 있다.

![image](https://github.com/muyaaho/spring-basic/assets/76798969/a17f8c77-3db0-4b63-8ad0-04f99b81ec10)


![image](https://github.com/muyaaho/spring-basic/assets/76798969/acc8376c-3370-49e9-a6cd-b0a8be223fb5)


위에 사진을 다시 가져왔는데 브랜치 모습을 보면 `origin/main`과 `main`이 떨어져 있어 별도의 브랜치로 커밋되는 것을 확인 할 수 있다. 다음에 새로 레퍼지토리 만들 때 확인하고 해결 방법을 업그레이드 하자. 브랜치를 잘 확인하고 커밋하는 습관을 들이자. (중요)
