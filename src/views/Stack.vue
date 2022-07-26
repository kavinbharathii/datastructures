<script>
let id = 0

export default {
    name: 'Stack',
    data() {
        return {
            pushItem: '',
            stack: [],
        }
    },
    methods: {
        pushStack() {
            if (this.pushItem !== "") {
                this.stack.push({ id: id++, text: this.pushItem })
                this.pushItem = ''
            } else {
                alert("Required field")
            }
        },
        popStack() {
            // this.stack = this.stack.filter((t) => t !== todo)
            this.stack.pop()
        }
    }
}
</script>

<template>
<div id="stack">
    <div class="form-container">
        <h1>Stack</h1>
        <!-- <form @submit.prevent="pushStack"> -->
        <form>
            <input v-model="pushItem" class="input-field">
            <button class="submit-button red" @click.prevent="pushStack">Push</button>
            <button class="submit-button blue" @click.prevent="popStack">Pop</button>
        </form>
    </div>
    <div class="stack-view">
        <div v-for="todo in stack" :key="todo.id" class="stack-element">
            <p class="stack-element-p">{{ todo.text }}</p>
            <p class="stack-element-p">{{ stack.indexOf(todo) }}</p>
            <!-- <button @click="popStack(todo)">X</button> -->
        </div>
    </div>  
</div>
</template>

<style>
#stack {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
}

.input-field,
.submit-button {
    width: 100%;
    border: 2px solid var(--secondary);
    box-shadow: none;
    margin: 0.8em;
    border-radius: 10px;
}

.form-container,
.stack-view {
    width: 50%;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 10px;
}


.stack-element {
    display: flex;
    justify-content: space-between;
    width: 80%;
    padding: 20px;
    background: var(--secondary);
    border-radius: 10px;
    font-weight: 800;
    transition: 500ms ease;
}

.stack-element-p {
    color: var(--accent);
    background-color: transparent;
}

.red {
    background-color: var(--red);
}

.blue {
    background-color: var(--blue);
}

@media only screen and (max-width: 700px) {
    #stack {
        flex-direction: column;
    }

    .form-container,
    .queue-view,
    .stack-element {
        width: 85vw;
    }
}
</style>
