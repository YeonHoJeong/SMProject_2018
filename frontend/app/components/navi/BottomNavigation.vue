<template>
    <StackLayout orientation="horizontal" row="1" id="navigation">
        <Label width="25%" class="fa" :text="'fa-eye' | fonticon" @tap="$navigateTo(router_list.one)" />
        <Label width="25%" class="fa" :text="'fa-heart' | fonticon" @tap="talk()"/>
        <Label width="25%" class="fa" :text="'fa-user' | fonticon" />
        <Label width="25%" class="fa" :text="'fa-user' | fonticon" />
        <!-- 각각의 라벨 터치 할때마다 최상위 부모의 currentView 값 수정 -->
    </StackLayout>
</template>

<script>
    import _ from 'lodash'
    import { mapState } from 'vuex'
    import { apiPath } from '../../lib/httpconfig'
    import axios from 'axios'
    import app from '../App'
    export default {
        name: "BottomNavigation",
        data(){
            return{
                router_list: {
                    one: app
                    // two: test
                }
            }
        },
        methods: {
            talk: function(){
                // console.log("test");
                axios.get(apiPath.android+'/temp')
                    .then(function (response) {
                        console.log("");
                        console.log(response.data);
                    })
                    .catch(function (error) {
                        console.log(error);
                    });
                // axios.get(apiPath.ios+'/temp')
                //     .then(function (response) {
                //         console.log("");
                //         console.log(response.data);
                //     })
                //     .catch(function (error) {
                //         console.log(error);
                //     });
            }
        }
    }
</script>

<style scoped>
    #navigation {
        background-color: aquamarine;
    }

    #navigation Label {
        text-align:center;
        font-size: 25%;
        color: darkslategray;
        vertical-align: middle;
        /*hover*/
    }
</style>
