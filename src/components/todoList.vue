<template>
	<!-- <div>list
	</div> -->

	<section>
		<ul>
			<li v-for="(todoItem,index) in todoItems" :key="todoItem" class="shadow">
				<i class="checkBtn fas fa-check" aria-hidden="true"></i>
					{{ todoItem }} 
				<span class="removeBtn" type="button" @click="removeTodo(todoItem, index)"> <!--@click은 v-on:click 과 동일함-->
					<i class="far fa-trash-alt" aria-hidden="true"></i>
				</span>

			</li>
		</ul>
	</section>

</template>

<script type="text/javascript">
export default{
	data(){
		return {
			todoItems: []
		}
	},
	created(){ //beforeMount , mounted 등 라이프 사이클에 진행해도 결과 동일하나 추후 코드 구조 개선하고 나면 화면 렌더링에 문제가 생김 
		var len = localStorage.length ;
		if( len > 0){
			for( var i=0 ; i< len ; i++){
				this.todoItems.push(localStorage.key(i));


			}
		}
	},
	methods:{
		removeTodo(todoItem, index){
			//console.log(todoItem, index)
			localStorage.removeItem(todoItem);
			this.todoItems.splice(index,1); // splice = 인자로 받은 인덱스를 이용해 배열의 해당 인덱스에서 1만큼 삭제함 
			//삭제하자마자 뷰에서 자동으로 화면을 갱신함 왜냐. ? 데이터 속성이 변하면 화면에 즉시 반영하는 뷰의 반응성 때문 ~!
		}
	}

}
</script>

<style scoped>
  ul {
    list-style-type: none;
    padding-left: 0px;
    margin-top: 0;
    text-align: left;
  }
  li {
    display: flex;
    min-height: 50px;
    height: 50px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 5px;
  }
  .checkBtn {
    line-height: 45px;
    color: #62acde;
    margin-right: 5px;
  }
  .removeBtn {
    margin-left: auto;
    color: #de4343;
  }

  .list-enter-active, .list-leave-active {
    transition: all 1s;
  }
  .list-enter, .list-leave-to {
    opacity: 0;
    transform: translateY(30px);
  }
</style>