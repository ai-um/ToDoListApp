<template>
  <h4>Список дел</h4>
  <div class="tasks">
    <div 
    class="task"
      :class="{
        completed: task.isCompleted 
      }"
      v-for="task in tasks" 
      :key="task._id"
      @click="completedHandler(task._id)"
    >
      <div 
      class="round"
        :class="{
          business: task.type == 'business', 
          personal: task.type == 'personal' 
        }">
      </div>
      
      <span>{{task.name}}</span>
    </div>
  </div>

  <div class="add-task">
    <input type="text" placeholder="Название задачи" v-model="taskName">
    <select name="typeOfATask" id="typeOfATask" v-model="tasks.type">
      <option value="personal">personal</option>
      <option value="business">business</option>
    </select>
    <button @click="addTask">+</button>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

// строки ниже взяты отсюда: https://vueframework.com/docs/v3/ru/ru/guide/state-management.html#простои-контеинер-состояния-с-нуля
export default {
  name: 'App',
  data() {
    return {
      taskName: '',
      tasks: [ // на этот tasks мы ссылаемся в строке 4.
        { 
          _id: 'fdsfdsd1',
          name: 'Приложение «Список дел»',
          isCompleted: false,
          type: 'business'
        },
      ],
    };
  },
  methods: {
    completedHandler: function (taskId) {
      // console.log(taskId); // для отладки
      const currentTask = this.tasks.find(t=>t._id === taskId);
      currentTask.isCompleted = !currentTask.isCompleted;
    },

    addTask: function() {
      this.tasks.push({
        _id: Math.random().toString(36).substring(2, 7),
        name: this.taskName,
        isCompleted: false,
        type: this.tasks.type,
      });
      //console.log(this.taskName); // для отладки
    },

  }
};
</script>

<!-- Задача: Изучить основы Vue.js и создать простое приложение для составления списка 
дел.
Критерии оценивания:
- Создайте новый проект Vue.js.
- Подключитесь и получите данные с помощью открытого API к 
https://jsonplaceholder.typicode.com/ (или к любому свободному API)
- Создайте новый компонент для отображения списка дел.
- Используйте директиву v-for для вывода списка дел из массива.
- Добавьте компонент формы для добавления новых пунктов в список дел.
- С помощью директивы v-model привяжите поле ввода к свойству data.
- С помощью директивы v-on обработайте событие отправки формы и добавьте новый 
элемент в список.
- Добавьте кнопку для удаления элементов из списка.
- С помощью директивы v-on обработайте событие нажатия на кнопку и удалите 
элемент из списка.
- Добавьте функцию сортировки и фильтрации списка.
- Оформите приложение с помощью CSS, чтобы сделать его визуально 
привлекательным.
- Реализуйте приложение с помощью чистого и читабельного кода на JavaScript.
- Тщательно протестируйте приложение, чтобы убедиться, что оно работает так, как 
ожидалось.
Результат работы выложите в виде ссылки на git 

-->