<template>
  <input v-model="width" placeholder="ширина" type="text">
  <input v-model="height" placeholder="высота" type="text">

  <div>Площадь прямоугольника: <input v-model="square" /></div> <!--Для вывода площади используем вычисляемое свойство, для записи - input-->
  <button @click="activate">Ok</button>  <!--@ - это сокращение v-on-->
  <div :class="{box:true, active: isActive}"></div>

  <ul>
    <li v-bind:key="i" v-for="item, i of list">{{ item }}</li> <!--перебор через i для правильного перебора массива, отрисовка изменяемых в массиве элементов-->
  </ul>
</template>

<script>
  export default { // экспортируем из app.vue объект по умолчанию
    name: "App", // Название компонета
    data() { // Состояние компонента, метод, который возвращает начальное состояние объекта
      return{
        width: 10,
        height: 10,

        isActive: false,
        list: ['первый', 'второй', 'третий']
      }
    },    
    computed: { // Вычисляемое свойство (площадь). Должно использовать хотя бы одно поле из состояния компонента data(){}      
      // square(){ // только чтение
      //   return this.height*this.width
      // }
      square: { // чтение и запись
        get() {return this.width * this.height},
        set(v) { this.width = Math.sqrt(v), this.height = Math.sqrt(v)} // v - то, что пользователь внёс в input площади
      }
    },
    methods: { // функции компонента
      activate(){
        this.isActive = !this.isActive;
      }
    },
    watch: { // Объект-наблюдатель за isActive
      isActive(oldV, newV){ 
        console.log(`старое значение: ${oldV}, новое: ${newV}`);
      }
    },
    props: { // входные параметры компонета, может быть массивом, каждый эл. которого - параметр
      type: String, // ограничиваем типом данных
      required: false, // если true, то title - это обязательный параметр
      default: '' // значение параметра по умолчанию (если он не будет передан)
    },
    beforeMount(){ // хук перед подключением объекта

    },
    mounted(){ // хук подключённого объекта

    },
    beforeUpdate(){ // хук при изменении данных, перед обновлением

    },
    update(){ // хук вызывается после того, как обновится виртуальный DOM из-за изменений данных

    }
  }
</script>

<style scoped>
  .box{
    width: 50px;
    height: 50px;
    border: 2px solid black;
  }
  .active{
    background-color: aqua;
  }
</style>
