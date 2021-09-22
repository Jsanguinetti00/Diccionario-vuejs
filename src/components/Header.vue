<template>
  <header className="header">
            <p className="name">
                {{name}}
            </p>
    </header>
</template>

<script>
export default {
 name:"Header",
 props:{
     name:String,
 }
}
</script>

<style scoped>
.header{
    background-color: #6443D9;
    height: 20px;
    width: 100%;
    left: 0px;
    position: fixed;
    top: 0;
    z-index: 10;
    display: flex;
    align-items: center;
    justify-content: flex-start;
    padding: 15px;
}

.name{
    color: #fff;
    margin: 0;
    font-weight: 500;
    font-size: 1.3rem;
}
</style>