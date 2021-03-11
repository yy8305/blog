# 라이브 방송관련 내용

## hls(m3u8) 동영상 view에 표시

- [hls.js cdn](https://cdnjs.com/libraries/hls.js/0.5.14)

- [hls.js github](https://github.com/video-dev/hls.js/)

- [video 태그 옵션 참고](https://videojs.com/city)


## 채팅창 view에 표시

socket.io-client, vue 사용

- [socket.io-client npm](https://www.npmjs.com/package/socket.io-client)

- view에서 
    ```javascript
    import { io } from "socket.io-client";

    const socket = io(url, {
        query: "rid=11&uid=111&nickname=" + encodeURIComponent("test")
    });

    //채팅서버 연결 (해당 함수는 채팅서버에서 이벤트를 보내줄때 실행됨)
    socket.on("connect", function(json) {
        console.log("socket connect : ", json);
    });

    //채팅서버로 파라미터 보내기
    socket.emit('hello', {message: 'test'});

    socket.connect();
    ```