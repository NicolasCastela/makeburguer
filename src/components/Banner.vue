<template>
    
    <id id="main-banner">
        <h1>Make Your Burguer</h1>
    </id>
</template> 


<script>
export default {
    name:'Banner'
}
</script>

<style scoped>

#main-banner{
    background-image: url('/public/img/burger.jpg');
    background-position: 100%;
    height: 500px;
    display: flex;
    align-items: center;
    justify-content: flex-start;  
    background-size: cover;
    
}
#main-banner h1{
    color: #FFF;
    text-align: center ;
    font-size: 60px;
    background-color: #222;
    padding: 20px 40px;

}


 </style>