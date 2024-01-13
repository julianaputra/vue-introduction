<template>
    <div class="todo-item">
        <h3>{{ todo }}</h3>
        <button @click="deleteTodo(index)">Delete</button>
    </div>
</template>

<script setup>
defineProps({
    todo: {
        type: String,
        required: true
    },
    index: {
        type: Number,
        required: true
    }
})

const emit = defineEmits(['delete'])

const deleteTodo = (index) => {
    emit('delete', index)
}
</script>