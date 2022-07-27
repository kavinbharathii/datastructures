<script>
let id = 0

export default {
    name: 'Queue',
    data() {
        return {
            pushItem: '',
            queue: [],
        }
    },
    methods: {
        pushqueue() {
            if (this.pushItem !== "") {
                this.queue.push({ id: id++, text: this.pushItem })
                this.pushItem = ''
            } else {
                alert("Required field")
            }
        },
        popqueue() {
            this.queue = this.queue.splice(1)
        }
    }
}
</script>

<template>
<div id="queue">
    <div class="form-container">
        <h1>Queue</h1>
        <!-- <form @submit.prevent="pushqueue"> -->
        <form>
            <input v-model="pushItem" class="input-field">
            <button class="submit-button red" @click.prevent="pushqueue">enqueue</button>
            <button class="submit-button blue" @click.prevent="popqueue">dequeue</button>
        </form>
    </div>
    <div class="queue-view">
        <div v-for="todo in queue" :key="todo.id" class="queue-element">
            <p class="queue-element-p">{{ todo.text }}</p>
            <p class="queue-element-p">{{ queue.indexOf(todo) }}</p>
            <!-- <button @click="popqueue(todo)">X</button> -->
        </div>
    </div>  
</div>
</template>

<style>
#queue {
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
    padding: 0.2em;
}

.form-container,
.queue-view {
    width: 50%;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 10px;
}


.queue-element {
    display: flex;
    justify-content: space-between;
    width: 80%;
    padding: 20px;
    background: var(--secondary);
    border-radius: 10px;
    font-weight: 800;
    transition: 500ms ease;
}

.queue-element-p {
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
    #queue {
        flex-direction: column;
    }

    .form-container,
    .queue-view,
    .stack-element {
        width: 85vw;
    }
}
</style>
