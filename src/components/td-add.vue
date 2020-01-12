<template>
    <div class="todo-container">
        <div class="todo-add">
            <input type="text" v-model.trim="newTodo" @keyup.enter="addItem(newTodo)">
            <button @click="addItem(newTodo)">add</button>
        </div>
        <ul class="todo-list">
            <li class="todo-list__item" v-for="(item, index) in items"
                v-bind:key="index">
                <input type="checkbox"
                       :id="'check'+index">
                <label :for="'check'+index"
                       v-if="isEditable!==index"
                >{{item}}
                </label>
                <input type="text"
                       v-if="isEditable===index"
                       v-model="editTodo"
                       @keyup.enter="editDoneItem(index)">
                <button @click="editItem(index)"
                        v-if="isEditable!==index">edit
                </button>
                <button @click="editDoneItem(index)"
                        v-if="isEditable==index">done
                </button>
                <button @click="removeItem(index)">remove</button>
            </li>
        </ul>
    </div>
</template>

<script>
    export default {
        name: "td-add",
        data() {
            return {
                newTodo: '',
                editTodo: false,
                isEditable: 'no',
                items: []
            }
        },
        methods: {
            addItem(val) {
                val.replace(/\s+/g, '');
                if (!val) {
                    return
                }
                this.items.unshift(val);
                this.newTodo = '';
            },
            editItem(val) {
                this.isEditable = val;
                this.editTodo = this.items[val];

            },
            editDoneItem(val) {
                this.isEditable = 'no';
                this.items[val] = this.editTodo;
                this.editTodo = '';
            },
            removeItem(val) {
                this.isEditable = 'no';
                this.items.splice(val, 1);
            }
        }
    }
</script>
