<template>
    <table v-if="meetings.length > 0">
        <thead>
            <tr>
                <th>Nazwa spotkania</th>
                <th>Opis</th>
                <th>Uczestnicy</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="meeting in meetings" :key="meeting.name">
                <td>{{ meeting.name }}</td>
                <td>{{ meeting.description }}</td>
                <td></td>
                <td><button @click="deleteMeeting()">Usuń spotkanie</button></td>
                <td><button>Zapisz się</button></td>
            </tr>
        </tbody>
    </table>
</template>

<script>
export default {
    props: ['meetings'],
    data() {
        return {
            deletedMeeting: {}
        }
    },
    methods: {
        deleteMeeting() {
            this.$emit('deleted', this.deletedMeeting);
            this.deletedMeeting = {};
        }
    }
}
</script>