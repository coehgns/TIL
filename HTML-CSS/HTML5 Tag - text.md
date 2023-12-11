# HTML5 Tag - text

## 1. 제목 (Headings) 태그

- Heading 태그는 제목을 나타낼 때 사용하며 h1 부터 h6 까지의 태그가 있다. h1이 가장 중요한 제목을 의미하며 글자의 크기도 가장큼.

```
<!DOCTYPE html>
<html>
    <body>
        <h1>heading 1</h1>
        <h2>heading 2</h2>
        <h3>heading 3</h3>
        <h4>heading 4</h4>
        <h5>heading 5</h5>
        <h6>heading 6</h6>
    </body>
</html>
```

- result

# heading 1

## heading 2

### heading 3

### heading 4

### heading 5

### heading 6

## 2. 글자 형태 (Text Formatting) 태그

### 2.1 b

- bold체를 지정함.
- 제목 태그와 같이 의미론적(Semantic) 중요성의 의미는 없다.

```html
<!DOCTYPE html>
<html>
    <body>
        <p>This text is normal.</p>
        <b>This text is bold.</b>
        <p style="font-weight: bold;">This text is bold.</p>
    </body>
</html>
```

- result

This text is normal.

**This text is bold.**

**This text is bold.**

### 2.2 strong

- b tag와 동일하게 bold체를 지정함.
- 의미론적(Semantic) 중요성의 의미를 갖음.

```
<!DOCTYPE html>
<html>
    <body>
        <p>This text is normal.</p>
        <strong>This text is strong.</strong>
    </body>
</html>
```

- result

This text is normal.

**This text is strong.**

### 2.3 i

- Italic체를 지정함.
- 의미론적(Semantic) 중요성의 의미 없음.

```
<!DOCTYPE html>
<html>
    <body>
        <p>This text is normal.</p>
        <i>This text is Italic.</i>
        <p style="font-style: italic;">This text is italic.</p>
    </body>
</html>
```

- result

This text is normal.

*This text is italic.*

*This text is italic.*

### 2.4 em

- emphasized(강조, 중요한) text를 지정함.
- i tag와 동일하게 Italic체로 표현됨.
- 의미론적(Semantic) 중요성의 의미를 갖음.

```
<!DOCTYPE html>
<html>
    <body>
        <p>This text is normal.</p>
        <em>This text is emphasized..</em>
    </body>
</html>
```

- result

This text is normal.

*This text is emphasized.*

### 2.5 small

- small text를 지정함.

```
<!DOCTYPE html>
<html>
    <body>
        <h2>HTML <small>Small</small> Formatting</h2>
    </body>
</html>
```

- result

**HTML Small Formatting**

### 2.6 mark

- highlighted text를 지정함.

```
<!DOCTYPE html>
<html>
    <body>
        <h2>HTML <mark>Small</mark> Formatting</h2>
    </body>
</html>
```

- result

  ![mark.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/9a39b38d-9826-4c70-9c64-ba63961aa014/mark.png)

### 2.7 del

- deleted (removed) text를 지정함.

```
<!DOCTYPE html>
<html>
    <body>
        <p>The del element represents deleted (removed) text.</p>
        <p>My favorite color is <del>blue</del> red.</p>
    </body>
</html>
```

- result

The del element represents deleted (removed) text.

My favorite color is blue red.

### 2.8 ins

- inserted (added) text를 지정함.

```
<!DOCTYPE html>
<html>
    <body>
        <p>The del element represents deleted (removed) text.</p>
        <p>My favorite <ins>color</ins> is red.</p>
    </body>
</html>
```

- result

  ![ins.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/482d1c54-3690-4a5d-842b-5d3d3efd9e9a/ins.png)

### 2.9 sub/sup

- sub 태그는 subscripted(아래에 쓰인) text를 sup 태그는 superscripted(위에 쓰인) text를 지정함.

```
<!DOCTYPE html>
<html>
    <body>
        <p>This is <sub>subscripted</sub> text.</p>
        <p>This is <sup>superscripted</sup> text.</p>
    </body>
</html>
```

- result

  ![sub-sup.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/58ecd018-9002-41e9-8adc-e933b8ad375c/sub-sup.png)

## 3. 본문 태그

### 3.1 p

- 단락(Paragraphs)을 지정함.

![p.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/4040e565-1bd1-4892-a977-38f6446d6a6a/p.png)

### 3.2 br

- br tag는 (강제) 개행 (line break)을 지정함
- br tag는 빈 요소(empty element)로 종료태그가 없다.

```
<!DOCTYPE html>
<html>
    <body>
        <p>This is <br>a para<br>graph with lin breaks</p>
    </body>
</html>
```

- result

This is

a para

graph with line breaks

### 3.3 pre

- 형식화된 text를 지정함.
- pre 태그 내의 content는 작성된 그대로 브라우저에 표시됨.

```
<!DOCTYPE html>
<html>
    <body>
        <p>HTML은 1개 이상의 연속된 공백(space)과 1개 이상의 연속된 줄바꿈(enter)을 1개의 공백으로 표시한다.</p>
        <pre>
            var myArray = [];
console.log(myArray.length); // 0

myArray[1000] = true;  // [ , , ... , , true ]

console.log(myArray.length); // 1001
console.log(myArray[0]);     // undefined
        </pre>
    </body>
</html>
```

- result

HTML은 1개 이상의 연속된 공백(space)과 1개 이상의 연속된 줄바꿈(enter)을 1개의 공백으로 표시한다.

```
var myArray = [];
console.log(myArray.length); // 0

myArray[1000] = true;  // [ , , ... , , true ]

console.log(myArray.length); // 1001
console.log(myArray[0]);     // undefined
```

### 3.4 hr

- 수평줄을 삽입함.

```
<!DOCTYPE html>
<html>
    <body>
        <h1>HTML</h1>
        <p>HTML is a language for describing web pages.</p>
        <hr>
        <p>CSS defines how to display HTML elements.</p>
    </body>
</html>
```

- result

# HTML

HTML is a language for describing web pages.

------

# CSS

CSS defines how to display HTML elements.

### 3.5 q

- 짧은 인용문을 지정함.
- 브라우저는 인용부호(큰따옴표)로 q 요소를 감싼다.

```
<!DOCTYPE html>
<html>
    <body>
        <p>Browsers usually insert quotation marks around the q element.</p>
        <p>WWF's goal is to: <q>Build a future where people live in harmony with nature.</q></p>
    </body>
</html>
```

- result

Browsers usually insert quotation marks around the q element.

WWF's goal is to: ”Build a future where people live in harmony with nature.”

### 3.6 blockquote

- 긴 인용문 블록을 지정함.
- 브라우저는 blockquote 요소를 들여쓰기함.

```
<!DOCTYPE html>
<html>
    <body>
        <p>Browsers usually indent blockquote elements.</p>
        <blockquote><p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolor 
            e magna aliqua.</p>
        </blockquote>
        </body>
</html>
```

- result

Browsers usually indent blockquote elements.

> Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.