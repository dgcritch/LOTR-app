<template>
    <div>
        <h3 v-for="quote in quotes" :key="quote._id">{{ quote.dialog }}</h3>
    </div>
</template>

<script>
import LotrService from '../services/LotrService';

export default {
    data () {
        return {
            quotes:[]
        }
    },
    created () {
        LotrService.getQuotes()
        .then ((response) => {
            this.quotes = response.data.docs;
        })
        .catch((error) => {
                console.error('Error fetching quotes:', error);
        });
    }
}
</script>