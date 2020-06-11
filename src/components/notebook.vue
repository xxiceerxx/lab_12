<template>
    <div class="Mob">
        <div>
            <p>Имя: </p>
            <input type="text" placeholder="" v-model="params.name"/>
        </div>
        <div>
            <p>Фамилия: </p>
            <input type="text" placeholder="" v-model="params.surname"/>
        </div>
        <div>
            <p>Отчество: </p>
            <input type="text" placeholder="" v-model="params.patronymic"/>
        </div>
        <div>
            <p>Номер: </p>
            <input type="text" placeholder="+7(   ) _ _ _" v-model="params.phone"/>
        </div>
        <div class="box">
            <p>Избранное </p>
            <input class="box" type="checkbox" v-model="params.favorite"/>
        </div>
        <div>
            <p>Сортировка</p>
           по Имени<input v-model="sort" value="n_a" type="radio"  v-on:click ="onSort('n_a')">
           по Фамилии<input v-model="sort" value="n_b" type="radio" v-on:click ="onSort('n_b')">
        </div>
        <div>
            <p>Добавление</p>
           <button v-on:click="onAdd()">Добавить</button>
        </div>
        <div>
            <h1 v-for="(item, index) in mas" v-bind:key=index>
            {{item.name}}
            {{item.surname}}
            {{item.patronymic}}
            {{item.phone}} <span v-if="item.favorite">+</span></h1>  
        </div>

        <!-- <button v-on:click="onLvUp">Повысить</button> -->
    </div>
</template>

<script>
export default {
    // props: {
    //     name: String,
    //     surname: String,
    //     patronymic: String,
    //     type: String
    // },
    name: "notebook",
    data(){
        return{
            // name: "Ivan",
            // surname: "Ivanov",
            // patronymic: "Ivanovi4"
            params: {
                name: "",
                surname: "",
                patronymic: "",
                phone: "",
                favorite: false
            },
            sort: "n_a",
            mas: [],
            flag: -1,
        }
    },
    methods: {
        // onLvUp(){
        //     this.$emit('lvUp', this.type);
        // }
        onSort: function (param){
            if(param === "n_a"){
                this.mas.sort((a, b) => a.name < b.name ? 1 : -1);
            }
            else if (param === "n_b"){
                this.mas.sort((a, b) => a.surname < b.surname ? 1 : -1);
            }
            this.mas.sort((a, b) => a.favorite < b.favorite ? 1 : -1);
        },
        onAdd: function (){
            if (this.flag === -1) {
                this.mas.push({
                    name: this.params.name,
                    surname: this.params.surname,
                    patronymic: this.params.patronymic,
                    phone: this.params.phone,
                    favorite: this.params.favorite
                });
            }
            else {
                this.mas[this.flag] = {
                    name: this.params.name,
                    surname: this.params.surname,
                    patronymic: this.params.patronymic,
                    phone: this.params.phone,
                    favorite: this.params.favorite
                };
                this.flag = -1;
            }
            if (this.sort === "n_a"){
                this.mas.sort((a, b) => a.name < b.name ? 1 : -1);
            }
            else if (this.sort === "n_b"){
                this.mas.sort((a, b) => a.surname < b.surname ? 1 : -1);
            }
            this.mas.sort((a, b) => a.favorite < b.favorite ? 1 : -1);
            this.params.name = "";
            this.params.surname = "";
            this.params.patronymic = "";
            this.params.phone = "";
            this.params.favorite = "";
        },
    }
};
</script>