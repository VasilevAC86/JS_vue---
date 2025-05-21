<template>
  <input v-model="width" placeholder="ширина" type="text">
  <input v-model="height" placeholder="высота" type="text">

  <div>Площадь прямоугольника: <input v-model="square" /></div> <!--Для вывода площади используем вычисляемое свойство, для записи - input-->
</template>

<script>
  export default { // экспортируем из app.vue объект по умолчанию
    name: "App", // Название компонета
    data() { // Состояние компонента, метод, который возвращает начальное состояние объекта
      return{
        width: 10,
        height: 10
      }
    },    
    computed: { // Вычисляемое свойство (площадь). Должно использовать хотя бы одно поле из состояния объекта      
      // square(){ // только чтение
      //   return this.height*this.width
      // }
      square: { // чтение и запись
        get() {return this.width * this.height},
        set(v) { this.width = Math.sqrt(v), this.height = Math.sqrt(v)} // v - то, чтов input площади
      }
    },
    methods: { // функции компонента

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

</style>
