    <script  lang="ts">
    
    import { defineComponent } from "vue";

    import type { PropType } from 'vue'
    
    export default defineComponent({

        props:{
            params: {
                type : Object as PropType<MenuTileParams>,
                require: true
                }
        }
    
    
    });
    

    interface MenuTileParams {
        picture?: string,
        menuTitle: string,
        preparationTime: string
    }
    </script>

<template>
    <div class="menu-tile-container">
        <div class="menu-tile-content">
            <div class="menu-tile-bloc">
                <div class="menu-tile-image">
                    <i>{{params ? params.picture: null}}</i>
                </div>
                <div class="menu-tile-info">
                    <div class="menu-name">
                        {{params ? params.menuTitle : null}}
                    </div>
                    <div class="menu-preparation-time">
                        {{params ? params.preparationTime : null}}
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>