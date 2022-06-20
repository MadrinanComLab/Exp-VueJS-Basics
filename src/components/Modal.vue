<template>
    <div class="backdrop">
        <div class="modal">
            <h1>Modal title</h1>
            <p>Modal Content</p>
        </div>
    </div>
</template>

<style scoped>/* scoped WILL LIMIT THE STYLESHEET AND ONLY AFFECT THIS COMPONENT (Modal.vue) */
.modal {
    width: 400px;
    padding: 20px;
    margin: 100px auto;
    background: #FFF;
    border-radius: 10px;
}

.backdrop {
    top: 0;
    position: fixed;
    background: rgba(0, 0, 0, 0.5);
    width: 100%;
    height: 100%;
}

h1 {
    color: red;
    border: none;
}
</style>