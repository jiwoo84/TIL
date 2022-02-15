# 1/25 cascading

## 문제점

---

```css
#login-form input:focus {
  border-color: var(--yellow);
}

#login-form input:not([type="submit"]) {
  border-bottom: 1px solid rgba(0, 0, 0, 0.2);
  transition: border-color 0.3s ease-in-out;
}
```

아래 `transition` 코드가 작동하지 않는 상황

## 원인

---

css의 cascading

- 중요도
- 명시도
- 코드 순서

세 번째 <코드 순서> 때문에 문제가 생겼다

`border-bottom` 이 구성되기도 전에 색상 설정(`input:focus`)이 작성되었기 때문

> `input:focus`를 먼저쓰면 색을 설정해줘도 `border`가 없으니 적용이 불가능하고, 그 이후에 `not`으로 `border-bottom`만 정의해주니 `focus`해도 색변화가 없습니다`input:not([type="submit"])`을 먼저쓰면 `border-bottom`이 정의되므로 `input:focus`에서 `border-color`가 `border-bottom`에 적용되어 원하는대로 나오는 것 같습니다
> 

## 해결

---

```css
#login-form input:not([type="submit"]) {
  border-bottom: 1px solid rgba(0, 0, 0, 0.2);
  transition: border-color 0.3s ease-in-out;
}

#login-form input:focus {
  border-color: var(--yellow);
}
```

위 아래 코드의 순서를 바꿔주면 된다

- 느낀점: 이해하고 나면 별거 아닌데, 원인을 찾기 은근 힘들었다.