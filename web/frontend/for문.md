# for문
구성
```java
  <element 이름 v-for="(value, index) in 변수 " :key="index">
```

적용 예제
```java
<template>
     <div
        class="agreement-content"
        v-for="(value, index) in info"
        :key="index"
      >
        <div
          class="agreement-content-title"
          @click="titleClickActive($event.target)"
        >
          <input type="checkbox" />
          {{ value.agreementTitle }}
          <div class="agreement-mg"></div>
        </div>
        <div class="agreement-content-info">
          {{ value.agreementContent }}
        </div>
      </div>
</template>
```
```java
<script>
  data() {
    info: []
  }
  method: {
    _load() {
      axios
        .request({
            ..
        })
        .then((res) => {
          this.info = res.data
        })
    },
  }
</script>
```
