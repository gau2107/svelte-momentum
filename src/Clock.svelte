<script>
    let curTime = null;
    setInterval(() => {
      let cur = new Date();
        curTime = cur.getHours().toString() +':'+ cur.getMinutes().toString();
    }, 1000);
</script>
<h1>{curTime}</h1>