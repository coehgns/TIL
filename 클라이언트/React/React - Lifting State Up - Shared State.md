<<<<<<< HEAD
# React - Lifting State Up - Shared State

# Lifting State Up

- 하위 컴포넌트의 state를 공통 상위 컴포넌트로 올리는 것.

------

# Shared State

- 자식 컴포넌트들이 가장 가까운 공통된 부모 컴포넌트의 스테이트를 공유해서 사용함.
- State에 있는 데이터를 여러 개의 하위 컴포넌트에서 공통적으로 사용하는 경우임.
- 하위 컴포넌트가 공통된 부모 컴포넌트의 state를 공유하여 사용하는 것.

------

## 하위 컴포넌트에서 State 공유하기

### 물의 끓음 여부를 알려주는 컴포넌트

```jsx
function BoilingVerdict(props) {
    if (props.celsius >= 100) {
        return <p>물이 끓습니다.</p>;
    }
    return <p>물이 끓지 않습니다.</p>;
}
```

- 섭씨온도 값을 props로 받아서 100°C 이상이면 물이 끓는다는 문자열을 출력하고 그 외에는 물이 끓지 않는다는 문자열을 출력함.

### 위 컴포넌트의 부모 컴포넌트

```jsx
function Calculator(props) {
    const [temperature, seTemperature] = useState( '' );

    const handleChange = (event) => {
        setTemperature(event.target.value);
    }

    return (
        <fieldset>
            <legend>섭씨 온도를 입력하세요:</legend>
            <input
                value={temperature}
                onChange={handleChange} />
            <BoilingVerdict
            celsius={parseFloat(temperature)} />
        </fieldset>
    )
}
```

- 사용자가 온도값을 변경할 때마다 HandleChange 함수가 호출됨.
- SetTemperature함수를 통해 온도값을 갖고 있는 Temperature라는 이름의 State를 업데이트함.
- State에 있는 온도값은 앞에서 만든 BoilingVerdict 컴포넌트에 Celsius라는 props로 전달됨.

------

## 완성된 TemperatureInput 컴포넌트

```jsx
function TemperatureInput(props) {
    const handleChange = (event) => {
        props.onTemperatureChange(evnet.target.value);
    }

    return (
        <fieldset>
            <legend>
                온도를 입력해 주세요(단위: {scaleNames[props.scale]});
            </legend>
            <input value={props.temperature} onChange={handleChange} />
        </fieldset>
    )
}
```

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113236
- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113237

=======
# React - Lifting State Up - Shared State

# Lifting State Up

- 하위 컴포넌트의 state를 공통 상위 컴포넌트로 올리는 것.

------

# Shared State

- 자식 컴포넌트들이 가장 가까운 공통된 부모 컴포넌트의 스테이트를 공유해서 사용함.
- State에 있는 데이터를 여러 개의 하위 컴포넌트에서 공통적으로 사용하는 경우임.
- 하위 컴포넌트가 공통된 부모 컴포넌트의 state를 공유하여 사용하는 것.

------

## 하위 컴포넌트에서 State 공유하기

### 물의 끓음 여부를 알려주는 컴포넌트

```jsx
function BoilingVerdict(props) {
    if (props.celsius >= 100) {
        return <p>물이 끓습니다.</p>;
    }
    return <p>물이 끓지 않습니다.</p>;
}
```

- 섭씨온도 값을 props로 받아서 100°C 이상이면 물이 끓는다는 문자열을 출력하고 그 외에는 물이 끓지 않는다는 문자열을 출력함.

### 위 컴포넌트의 부모 컴포넌트

```jsx
function Calculator(props) {
    const [temperature, seTemperature] = useState( '' );

    const handleChange = (event) => {
        setTemperature(event.target.value);
    }

    return (
        <fieldset>
            <legend>섭씨 온도를 입력하세요:</legend>
            <input
                value={temperature}
                onChange={handleChange} />
            <BoilingVerdict
            celsius={parseFloat(temperature)} />
        </fieldset>
    )
}
```

- 사용자가 온도값을 변경할 때마다 HandleChange 함수가 호출됨.
- SetTemperature함수를 통해 온도값을 갖고 있는 Temperature라는 이름의 State를 업데이트함.
- State에 있는 온도값은 앞에서 만든 BoilingVerdict 컴포넌트에 Celsius라는 props로 전달됨.

------

## 완성된 TemperatureInput 컴포넌트

```jsx
function TemperatureInput(props) {
    const handleChange = (event) => {
        props.onTemperatureChange(evnet.target.value);
    }

    return (
        <fieldset>
            <legend>
                온도를 입력해 주세요(단위: {scaleNames[props.scale]});
            </legend>
            <input value={props.temperature} onChange={handleChange} />
        </fieldset>
    )
}
```

------

## 참고 자료

- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113236
- https://www.inflearn.com/course/lecture?courseSlug=처음-만난-리액트&unitId=113237

>>>>>>> 88752f10985abb553e5666fa10794057c19770e8
------