<script>
import { getRandomUser } from "../api";
import Card from "./Card.vue";
export default {
    data() {
        return {
            users: []
        };
    },
    async mounted () { 
        const response = await getRandomUser(3)
        console.log(response.data)
        this.users = response.data
     },
     components: { Card }
}
</script>
<template>
    <div class="card-list">
        <Card 
        v-for="user of users"
        :imgUrl="user.avatar"
        :name="user.username"
        :description="user.date_of_birth"
        :key="user.id">
        </Card>
    </div>
</template>
<style>
.card-list{
    display: flex;
    gap: 15px;
}
</style>