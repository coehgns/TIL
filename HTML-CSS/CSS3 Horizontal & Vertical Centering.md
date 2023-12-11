# CSS3 Horizontal & Vertical Centering

## 1. 수평 정렬(Horizontal Align)

### 1.1 inline/inline-block 요소

- 정렬 대상 요소의 부모 요소에 text-align: center; 를 지정함.

```css
.container {
  text-align: center;
}
```

### 1.2 block 요소

- 정렬 대상 요소에 너비를 명시적으로 지정하고 margin-right와 margin-left 프로퍼티에 auto를 지정함.
- 정렬 대상 요소에 너비를 명시적으로 지정하지 않으면 너비는 full width가 되므로 중앙 정렬이 필요없음.

```css
.item {
   width: 200px;
   margin: 20px auto;
}
```

### 1.3 복수의 block 요소

- 복수의 block 요소는 기본적으로 수직 정렬됨.
- 수평 정렬하기 위해서는 정렬 대상 block 요소를 inline-block 요소로 변경한 후 부모 요소에 text- align: center; 를 지정함.
- 정렬 대상 요소에 width를 지정하지 않으면 콘텐츠에 너비에 맞추어 너비가 결졍되므로 명시적으로 너비를 지정함.

```css
.container {
  text-align: center;
}
.item {
  width: 150px;
  display: inline-block;
}
```

### 1.4 Flexbox

- flexbox를 사용할 수도 있음.(정렬 대상의 부모 요소에 아래의 룰셋을 선언함.)

```css
.flex-center {
   display: flex;
   justify-content: center;
}
```

## 2. 수직 정렬(Vertical Align)

### 2.1 inline/inline-block 요소

2.1.1 Single line

- 정렬 대상의 부모 요소에 padding-top과 padding-bottom 프로퍼티값을 동일하게 적용함.

```css
.container {
   padding: 50px;
}
```

- padding을 사용할 수 없는 경우, 요소의 height와 line-height 프로퍼티값을 동일하게 적용함.(단 여러 줄의 텍스트에는 사용할 수 없음.)

```css
.container {
   height: 100px;
   line-height: 100px;
}
```

### 2.1.2 Multiple lines

- 여러 줄의 텍스트의 경우, padding-top 과 padding-bottom 프로퍼티값을 동일하게 적용하는 방법도 가능함.(vertical-align 프로퍼티를 사용한 방법도 가능한데 이 방법은 table 속성을 사용하여야 함.)

```css
.parent {
  display: table;
  height: 100px;
}
.child {
  display: table-cell;
  vertical-align: middle;
}
```

### 2.1.3 Flexbox

```css
.container {
  display: flex;
  justify-content: center;
  flex-direction: column;
  height: 400px;
}
```

## 2.2 block 요소

### 2.2.1 요소의 높이가 고정되어 있는 경우

- 부모 요소를 기준으로 절대 위치를 지정함.

```css
.parent {
  position: relative;
}
.child {
  position: absolute;
  top: 50%;
  height: 100px;
  /*요소의 높이(100px)의 반 만큼 위로 이동*/
  margin-top: -50px;
}
```

### 2.2.2 요소의 높이가 불확정 상태의 경우

- 부모 요소를 기준으로 절대 위치를 지정함.

```css
.parent {
  position: relative;
}
.child {
  position: absolute;
  top: 50%;
  /*요소의 높이의 반(50%) 만큼 위로 이동*/
  transform: translateY(-50%);
}
```

### 2.2.3 Flexbox

- 부모 요소에 flexbox layout을 지정함.

```css
.parent {
  display: flex;
  /*위에서 아래로 수직 배치*/
  flex-direction: column;
  /*중앙정렬*/
  justify-content: center;
}
```

## 3. 수평/수직 정렬(Horizontal & Vertical Align)

- 요소의 너비와 높이가 고정되어 있는 경우, 요소의 너비와 높이가 불확정 상태의 경우 모두 사용 가능한 방법임.

```css
.parent {
  position: relative;
}
.child {
  position: absolute;
  top: 50%;
  left: 50%;
  /*요소의 높이/너비의 반(50%)만큼 위/왼쪽으로 이동*/
  transform: translate(-50%, -50%);
}
/* Flexbox를 사용한 방법 */
.parent {
  display: flex;
  justify-content: center;
  align-items: center;
}
```