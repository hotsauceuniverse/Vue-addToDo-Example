<template>
  <!-- 
  1. 타이틀 
  2. 텍스트 입력란 
  3. '추가하기' 버튼 생성 
  4. 입력란에 문자입력 시, 하단에 리스트 노출
  5. 리스트 목록에 각 삭제버튼 생성
  6. 삭제버튼 클릭 시, 목록 삭제 
  -->
  <div>
    <h2>Vue로 할 일 목록 만들기</h2>
      <form>
        <input type="text" class="list"/>
        <button @click="addList">일정 추가</button>
      </form>
      <ul>
        <li v-for="(list, index) in lists" :key="list">
          <p>
          {{ list.text }}
          <button @click="deleteList(index)">일정 삭제</button>
          </p>
        </li>
      </ul>
  </div>
</template>


<script>
  export default {

  methods: {
    addList(event) {
      event.preventDefault();
      const list = {
        text: document.querySelector('input.list').value,
      };
        this.lists.push(list);
    },

      deleteList(index) {
        this.lists.splice(index, 1);
      }
  },

  data() {
    return {
      lists: []
      }
    }
  }
</script>