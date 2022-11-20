<script lang="ts">
import { defineComponent } from 'vue'
import type { PropType } from 'vue'
import axios from 'axios'

interface Menu {
    title: string,
    picture?: string
    preparationTime :string
}
interface Menus {
    [key:number] : Menu 
}

export default defineComponent({
    setup() {
        
    },
    data(){
        return {
            menus: Object as PropType<Menus>,
            filter:null,
            errors:null
        }
    },
    async created(){
        await this.getAll();
    },
    methods:{
        async getAll(){
      
            const url = "http://127.0.0.1:9400/menus"
            
            // const response = await fetch(url,{
            //     method:'Get',
            //     mode:'no-cors',
            //     headers: {
            //     'Content-Type': 'application/json'
            //     // 'Content-Type': 'application/x-www-form-urlencoded',
            //     },
            // })
                fetch('http://localhost:9400/menus',{
                    headers:{
                        'Content-Type': 'application/json'
                    }
                })
                .then((response) => response.json())
                .then((data) => this.menus = data.body.data)
                .catch((err)=> this.errors = err.msg)
                ;
     
            //const res = await response.json()
        }
        
    }
})
</script>



<template>
    <div id="home-menu-container">
        <div id="home-menu-content">
            <div id="home-menu-content">
                
                <div id="filter-container">
                    <div id="filter-bloc">
                        <div id="filter-content">
                            <input type="text" id="filter-input" placeholder="entrez votre recherche" />
                        </div>
                    </div>
                </div>
                <div id="page-info-container">
                    <div id="page-info-bloc"> 
                        <div id="page-info-content">
                            <div id="page-info-filter-result-info">
                                <div>
                                    <h4>Result for ''{{filter}}''</h4>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
                <div id="page-filter-result-container">
                    <div id="page-filter-result-content">
                        <div id="page-filter-result">test
                            <template v-for="menu in menus" :key="menu.id">
                                
                            </template>
                        </div>
                    </div>
                </div>

                

            </div>
        </div>
    </div>
</template>
<style scoped>
    #filter-input{
        width: 100%;
        border: none;
        border: 1px solid rgb(228, 228, 228);
        padding: 1rem;
        border-radius: 1rem;
        font-size: 1.2em;
        font-weight: 400;
    }



    h4{
        color:black;
        font-size: 2em;
        font-weight: 600;
        margin-top: 1rem;
    }
</style>


