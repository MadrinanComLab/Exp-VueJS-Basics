<template>
    <div class="backdrop" @click="closeModal">
        <!--/ 
            REMEMBER:
            <div class="modal" :class="{ sale: theme == 'sale' }">
            THE ELEMENT BELOW WILL BE GIVEN A CLASSNAME OF 'sale' IF THE THEME IS EQUAL TO SALE 
            VALUE THAT WILL BE ASSIGNED  IF THIS CONDITION IS TRUE (I HOPE YOU GET WHAT I'M TRYING TO SAY)
                |                                |
                V                                V
               sale:                       theme == 'sale'
        /-->
        <div class="modal" :class="{ sale: theme == 'sale' }">
            <h1>{{ header }}</h1>
            <p>{{ text }}</p>

            <!--/ THE EXAMPLE LOOP BELOW DEMONSTRATE HOW TO ASSIGN UNIQUE ID TO ITS ITEM (<h4></h4>) /-->
            <!--<li v-for="(book, i) in books" :key="i">
                <h4 :id="'book' + i">{{ i }}.) "{{ book }}"</h4>
            </li> /-->
            
            <!--/ <li v-for="(author, i) in authors" :key="i">
                <h4 :id="'author' + i">{{ (i + 1) }}.) "{{ author }}"</h4>
            </li> /-->

            <!--/ <li v-for="book in books" :key="book.id"> FOR v-for TO WORK IN THIS SET UP YOU NEED THIS: :key="book.id"
                <h4>"{{ book.title }}" by {{ book.author }}</h4>
            </li> /-->
        </div>
    </div>
</template>

<script>
export default {
    // NOTE: IF YOU HAVE NEW PROPS DON'T FORGET TO REGISTER IT HERE FIRST...
    props: [ "header", "text", "fruits", "theme", "books", "authors" ], // THIS IS HOW WE RECEIVE PROPS OR DATA FROM OTHER COMPONENTS
    methods: {
        closeModal() {
            this.$emit("close") // USING THIS WE'RE BE ABLE TO COMMUNICATE TO PARENT COMPONENT AND HAVE ACCESS TO ITS FUNCTIONS
        }
    }
}
</script>

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

.modal.sale { /* THIS ANOTHER WAY LIMITING THE SCOPE OF YOUR CSS */
    background: crimson;
    color: #FFF;
}

.modal.sale h1 {
    color: #FFF;
}
</style>