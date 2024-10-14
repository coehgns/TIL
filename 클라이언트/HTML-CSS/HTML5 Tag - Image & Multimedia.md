## 1. 이미지

- 웹페이지에 이미지를 삽입하는 경우, img tag를 사용함.

| attribute | Description                                  |
| --------- | -------------------------------------------- |
| src       | 이미지 파일 경로                             |
| alt       | 이미지 파일이 없을 경우 표시되는 문장        |
| width     | 이미지의 너비 (CSS에서 지정하는 것이 일반적) |
| height    | 이미지의 높이 (CSS에서 지정하는 것이 일반적) |

```html
<!DOCTYPE html>
<html>
    <body>
        <img src="assets/images/doug.jpg" alt="doug" width="100">
        <img src="assets/images/wrongname.gif" alt="이미지가 없습니다.">
    </body>
</html>
```

- result

  ![images.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/1f3845b6-eb70-4a57-a720-3baa645e347c/images.png)

## 2. 미디어

### 2.1 audio

- audio 태그는 HTML5에서 새롭게 추가된 태그이며 IE8 이하에서는 사용 할 수 없음.

| attribute | Description                                                  |
| --------- | ------------------------------------------------------------ |
| src       | 음악 파일 경로                                               |
| preload   | 재생 전에 음악 파일을 모두 불러올 것인지 지정                |
| autoplay  | 음악 파일을 자동의 재생 개시할 것인지 지정                   |
| loop      | 음악을 반복할 것인지 지정                                    |
| controls  | 음악 재생 도구를 표시할 것인지 지정. 재생 도구의 외관은 브라우저마다 차이가 있다. |

```html
<!DOCTYPE html>
<html>
    <body>
        <audio src="assets/audio/Kalimba.mp3" controls></audio>
    </body>
</html>
```

- result

  ![audio.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/9171b954-b250-4f49-ac9e-0a079b7e5e59/audio.png)

- 웹브라우저 별로 지원하는 음악 파일 형식이 다름.

- 파일 형식에 따라 재생되지 않는 브라우저가 존재한다는 뜻.

- source 태그를 사용하여 파일 형식의 차이 문제를 해결 할 수 있음.

- type 어트리뷰트는 생략 가능함.

| Browser           | MP3      | Wav  | Ogg  |
| ----------------- | -------- | ---- | ---- |
| Internet Explorer | YES      | NO   | NO   |
| Chrome            | YES      | YES  | YES  |
| Firefox           | YES(24~) | YES  | YES  |
| Safari            | YES      | YES  | NO   |
| Opera             | YES(25~) | YES  | YES  |

```
<!DOCTYPE html>
<html>
    <body>
        <audio controls>
            <source src="assets/audio/Kalimba.mp3" type="audio/mpeg">
            <source src="assets/audio/Klimba.ogg" type="audio/ogg">
        </audio>
    </body>
</html>
```

- result

  ![audio.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/8f2e0a51-1400-4d9f-bf5d-4f83ed2e89eb/audio.png)

### 2.2 비디오

- video 태그는 HTML5에서 새롭게 추가된 태그임.
- IE8 이하에서는 사용 할 수 없음.

| attribute | Description                                                  |
| --------- | ------------------------------------------------------------ |
| src       | 동영상 파일 경로                                             |
| poster    | 동영상 준비 중에 표시될 이미지 파일 경로                     |
| preload   | 재생 전에 동영상 파일을 모두 불러올 것인지 지정              |
| autoplay  | 동영상 파일을 자동의 재생 개시할 것인지 지정                 |
| loop      | 동영상을 반복할 것인지 지정                                  |
| controls  | 동영상 재생 도구를 표시할 것인지 지정. 재생 도구의 외관은 브라우저마다 차이가 있다. |
| width     | 동영상의 너비를 지정                                         |
| height    | 동영상의 높이를 지정                                         |

- audio 태그와 마찬가지로 파일 형식의 차이 문제가 발생 할 수 있음.
- sourc 태그르 사용하여 형식 차이 문제를 해결함. type 어트리뷰트는 생략 가능.

| Browser           | MP4      | WebM | Ogv  |
| ----------------- | -------- | ---- | ---- |
| Internet Explorer | YES      | NO   | NO   |
| Chrome            | YES      | YES  | YES  |
| Firefox           | YES(21~) | YES  | YES  |
| Safari            | YES      | NO   | NO   |
| Opera             | YES(25~) | YES  | YES  |

```html
<!DOCTYPE html>
<html>
    <body>
        <video width="640" height="360" control>
            <source src="assets/video/wildlife.mp4" type="video/mp4">
            <source src="assets/video/wildlife.webm" type="video/webm">
        </video>
    </body>
</html>
```

- result

  ![video.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/510cd684-c9a0-45bd-b45d-b35ad6027628/971c8c64-6f36-4744-bf53-dc5bd99d2ced/video.png)