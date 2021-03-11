# javascript 문법 정리

## 유용한 함수

### 숫자 앞에 0 붙이기

```javascript
function numberPad(n, width) {
    n = n + '';
    return n.length >= width ? n : new Array(width - n.length + 1).join('0') + n;
}
```

### moment로 시간 차이 구하기

```javascript
let t1 = moment(test_time)); //지정시간
let t2 = moment(); // 현재시간

//현재시간 - 지정시간
let diffTime = {
    day : moment.duration(t2.diff(t1)).days(),
    hour : moment.duration(t2.diff(t1)).hours(),
    minute : moment.duration(t2.diff(t1)).minutes(),
    second : moment.duration(t2.diff(t1)).seconds()
}

# 시간:분:초
timeStr = diffTime.hour,2 + ':' + diffTime.minute,2 + ':' + diffTime.second,2;
```