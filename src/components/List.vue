<template>
      
        <!-- v-if ou v-else suivant sur true ou false afin d'ajouter (add)
        ou de modifier (updateTodo) -->

        <div v-if="!isEditing">
            <!-- ! différent de -->
            <input type='text' v-model="todo">
            <!-- V-MODEL : v-model crée une liaison de données sur les champs de formulaire 
            (input, select ou textarea) -->
            <input class="typebutton" type='submit' value="add" @click="storeTodo">
        </div>
     
        <div v-else>
            <input type='text' v-model="todo">
            <input class="typebutton" type='submit' value="update" @click="updateTodo">
        </div>

        <ol>
            <!-- Affiche notre liste -->
            <li class="textwhite" v-for="(todo, index) in todos" :key="todo">
                {{ todo }}
                <button @click="editTodo(index, todo)">Edit</button>
                <button @click="deleteTodo(index)">Delete</button>
            </li>
        </ol>
</template>

<script>

export default {
    //data : Permet que les données et le DOM soient couplés
    data: () => {
        return {
            isEditing: false,
            selectedIndex: null,
            todo: '',
            todos: ['Learn Vue.js', 'Love chocolate'],
        }
    },
    methods: {
        //METHODES :
        // Les méthodes vous permettent de définir des fonctions auxquelles 
        // votre application Vue aura accès. 
        // Elles sont définies comme la propriété  data.
        
         // relie le bouton storeTodo
        storeTodo() {
            //Bouton qui permet d'ajouter des éléments à la liste

            // THIS : this est un opérateur qui permet de retourner 
            //une valeur en fonction de son contexte. 
            //this retourne l’objet 

            // PUSH : méthodes encapsulées qui va permettre d'ajouter 
            // des nouveaux élements ds la liste todos

            this.todos.push(this.todo)
            this.todo =''

            //Ajoute les nouveaux élements dans le tableau todos
            console.log('store todos');
            console.log(this.todos);
        },

        //Permet de relier le bouton editTodo, bouton qui édite la liste
         editTodo(index, todo) {
            this.todo = todo
            this.selectedIndex = index
            this.isEditing = true
        },

        //le bouton add qui devient update afin de renvoyer le liste modifiée
        updateTodo() {
            //SPLICE : la méthode splice() permet d'insérer un élement à la place d'un autre
            //cette méthode écrase une tranche du tableau par une autre, splice attend un nombre,
            //ici splice supprime this.selectedIndex pour le remplacer par this.todo
            this.todos.splice(this.selectedIndex, 1, this.todo)
            this.isEditing = false
          
            //une fois que l'élement à été changé via update il repasse sur false
            //pour que notre bouton add revienne
        },

            //Bouton delete
        deleteTodo(index) {
        this.todos.splice(index, 1)
            //supprime un élement de l'index
    }
    }
}
</script>

<style>

    /* TO DO LIST STYLE*/

    button, .typebutton{
        background-color:rgb(228, 132, 22);
        border:none;
        border-radius: 20px;
        padding: 1.2rem 1.2rem;
        margin: 1rem 1rem;
        font-family: 'Satisfy', cursive;
        font-size: 1.5rem;
        color: white;
    }

    .textwhite{
        font-size: 1.5rem;
        font-family: 'IBM Plex Mono', monospace;
        color: white;
    }

</style>