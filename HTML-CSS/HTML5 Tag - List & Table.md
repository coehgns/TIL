# HTML5 Tag - List & Table

## 1. 목록 (List)

### 1.1 순서없는 목록 (Unordered List)

```
<!DOCTYPE html>
<html>
    <body>
        <h2>순서없는 목록 (Unordered List)</h2>
        <ul>
            <li>Coffee</li>
            <li>Tea</li>
            <li>Milk</li>
        </ul>
    </body>
</html>
```

- result

## 순서없는 목록 (Unordered List)

- Coffee
- Tea
- Milk

### 1.2 순서 있는 목록 (Ordered List)

```
<!DOCTYPE html>
<html>
    <body>
        <h2>순서있는 목록 (Unordered List)</h2>
        <ol>
            <li>Coffee</li>
            <li>Tea</li>
            <li>Milk</li>
        </ol>
    </body>
</html>
```

- result

## 순서있는 목록 (Ordered List)

1. Coffee
2. Tea
3. Milk

- type 어트리뷰트를 사용하여 순서를 나타내는 문자를 지정할 수 있음.

| Value | Description     |
| ----- | --------------- |
| “1”   | 숫자 (기본값)   |
| “A”   | 대문자 알파벳   |
| “a”   | 소문자 알파벳   |
| “I”   | 대문자 로마숫자 |
| “i”   | 소문자 로마숫자 |

```html
<ol type="I">
            <li value="2">Coffee</li>
            <li value="4">Tea</li>
            <li>Milk</li>
        </ol>
```

- result

II. Coffee

IV. Tea

V. Milk

- start 어트리뷰트로 리스트의 시작값을 지정할 수 있음.

```
<ol start="3">
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ol>
```

- result

1. Coffee
2. Tea
3. Milk

- reverse 어트리뷰트를 지정하면 리스트의 순서값을 역으로 표현함.

```
<ol reversed>
   <li>Coffee</li>
   <li>Tea</li>
   <li>Milk</li>
</ol>
```

- result

1. Coffee
2. Tea
3. Milk

### 1.3 중첩 목록

```
<!DOCTYPE html>
<html>
    <body>
        <h2>중첩 목록</h2>
        <ul>
            <li>Coffee</li>
            <li>Tea
                <ol>
                    <li>Black tea</li>
                    <li>Green tea</li>
                </ol>
            </li>
            <li>Milk</li>
        </ul>
    </body>
</html>
```

- result

## 중첩 목록

- Coffee
- Tea
  1. Black tea
  2. Green tea
- Milk

## 2. 테이블

- 표(table)를 만들 때 사용하는 태그임.

| tag   | Description                       |
| ----- | --------------------------------- |
| table | 표를 감싸는 태그                  |
| tr    | 표 내부의 행 (table row)          |
| th    | 행 내부의 제목 셀 (table heading) |
| td    | 행 내부의 일반 셀 (table data)    |

![table.gif](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/cb4aa9b5-d546-4851-b07d-e9ae52442ff7/table.gif)

```html
<!DOCTYPE html>
<html>
    <body>
        <table border="1">
            <tr>
                <th>First name</th>
                <th>Last name</th>
                <th>Score</th>
            </tr>
            <tr>
                <td>Jill</td>
                <td>Smith</td>
                <td>50</td>
            </tr>
            <tr>
                <td>Eve</td>
                <td>Jackson</td>
                <td>94</td>
            </tr>
            <tr>
                <td>John</td>
                <td>Doe</td>
                <td>80</td>
            </tr>
        </table>
    </body>
</html>
```

- result

  ![table.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/594d137a-f467-4b5a-a788-983bdd740e25/table.png)

- 테이블 태그의 어트리뷰

| attribute | Description                                                  |
| --------- | ------------------------------------------------------------ |
| border    | 표 테두리 두께 지정. (CSS border property를 사용하는 것이 더 나은 방법이다.) |
| rowspan   | 해당 셀이 점유하는 행의 수 지정                              |
| colspan   | 해당 셀이 점유하는 열의 수 지정                              |

```html
<!DOCTYPE html>
<html>
    <head>
        <style>
            table, th, td {
                border: 1px slid black;
                border-collapse: collapse;
            }
            th, td {
                padding: 15px;
            }
        </style>
    </head>
    <body>
        <h2>2개의 culumn을 span</h2>
        <table>
            <tr>
                <th>Name</th>
                <th colspan="2">Telephone</th>
            </tr>
            <tr>
                <td>Bill gates</td>
                <td>555 77 854</td>
                <td>555 77 855</td>
            </tr>
        </table>

        <h2> 2개의 row를 span</h2>
        <table>
            <tr>
                <th>Name:</th>
                <td>Bill gates</td>
            </tr>
            <tr>
                <th rowspan="2">Telephone:</th>
                <td>555 77 854</td>
            </tr>
            <tr>
                <td>555 77 855</td>
            </tr>
        </table>
    </body>
</html>
```

- result

![rowspan-colspan.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/57dd52a1-d047-43e6-8eba-d092f6cc3f07/rowspan-colspan.png)