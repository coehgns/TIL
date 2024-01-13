# React - Form과 Controlled Component

------

# Form

- 사용자로부터 입력을 받기 위해 사용하는 것.

# Controlled Component

- 사용자가 입력한 값에 접근하고 제어할 수 있도록 해주는 컴포넌트.
- 값이 리액트의 통제를 받는 Input From Element임.
- 사용자의 입력을 직접적으로 제어할 수 있음.

------

## Form 종류

### Textarea 태그

- 여러 줄에 걸쳐 긴 텍스트를 입력받기 위한 HTML 태그.

```html
// HTML textarea 태그

<textarea>
     안녕하세요, 여기에 이렇게 텍스트가 들어가게 됩니다.
</textarea>
```

- React에서는 textarea 태그에 value라는 어트리뷰트를 사용하여 텍스트를 표시함.

### Select 태그

- Drop-down 목록을 보여주기 위한 HTML 태그.
  - Drop-donw 목록은 여러가지 옵션 중에서 하나를 선택할 수 있는 기능을 제고함.

```html
// HTML select 태그

<select>
    <option value = apple>사과</option>
    <option value = "banana">바나나</option>
    <option selected value = "grape">포도</option>
    <option value = "watermelon">수박</option> 
</select>    
```

- 옵션 태그에서 현재 선택된 옵션의 경우에는 Selected라는 어트리뷰트를 갖고 있음.
- React에서는 옵션 태그에 Selected 속성을 사용하지 않고 Select 태그에 Value라는 어트리뷰트를 사용해서 값을 표시함.

------

### File input 태그

- 디바이스의 저장 장치로부터 하나 또는 여러 개의 파일을 선택할 수 있게 해주는 HTML 태그.
- 서버로 파일을 업로드하거나 자바스크립트의 File API를 사용해서 파일을 다룰 때 사용함.

```html
// HTML file input 태그

<input type="file" />
```

- FileInput 태그는 그 값이 있기 전용이기 때문에 React에서는 통제를 받지 않음.

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113233
- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113234

------