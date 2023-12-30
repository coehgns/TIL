# JS Device Orientation Event

- Device Orientation은 중력과의 관계에서 디바이스의 물리적 방향의 변화를 감지할 수 있음.
- 모바일 디바이스를 회전시켰을 때 이벤트를 감지하여 적절히 화면을 변화 시킬 수 있음.

------

- 디바이스의 방향 정보를 다루는 자바스크립트 이벤트
  - DeviceOrientationEvent 가속도계가 기기의 방향의 변화를 감지했을 때 발생함.
  - DeviceMotionEvent 가속도에 변화가 일어났을 때 발생함.

```jsx
if (window.DeviceOrientationEvent) {
  // Our browser supports DeviceOrientation
} else {
  console.log('Sorry, your browser doesn't support Device Orientation');
}
```

# ***\*DeviceOrientationEvent\****

- 디바이스의 방향 변화는 3개의 각도(alpha, beta, gamma)를 사용하여 측정됨.
- deviceorientation 이벤트에 리스너를 등록하면 리스너 함수가 주기적으로 호출되어 업데이트된 방향 데이터를 제광함.

------

```jsx
// deviceorientation 4가지 이벤트

window.addEventListener('deviceorientation', handleOrientation, false);

function handleOrientation(event) {
  var absolute = event.absolute;
  var alpha    = event.alpha;
  var beta     = event.beta;
  var gamma    = event.gamma;

  // Do stuff with the new orientation data
}
```

- DeviceOrientationEvent.absolute
- DeviceOrientationEvent.alpha
- DeviceOrientationEvent.beta
- DeviceOrientationEvent.gamma

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/91b9c26f-3567-4747-b3e4-bc2f6f424b75/Untitled.png)

------

## absolute

- 지구좌표계를 사용하는 지에 대한 boolean 값임.

------

## alpha

- 0도 부터 360도까지 범위의 z축을 중심으로 디바이스의 움직임을 나타냄.

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/e9251479-2591-4bbf-ac40-7313c072ba17/Untitled.png)

------

## beta

- -180도 부터 180도까지 범위의 x축을 중심으로 디바이스의 움직임을 나타냄.(디바이스의 앞뒤 움직임을 나타냄.)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/f6956119-2495-4ec5-acd0-d20f4685c236/Untitled.png)

------

## gamma

- -90도부터 90도까지 범위의 y축을 중심으로 디바이스의 움직임을 나타냄.(디바이스의 좌우 움직임을 나타냄.)