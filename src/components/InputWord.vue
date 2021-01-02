<template>
    <div>
        <form @submit.prevent="">
            <div class="form-group">
                <input v-on:keyup="submitWord" id="inputText" type="text" name="newword" v-model="inputWord" placeholder="Enter word">
            </div>
            <!-- <button class="btn btn-primary" type="submit">Submit</button> -->
        </form>
    </div>
</template>
<script>
export default {
    name: 'InputWord',
    props: ['newLetter'],
    data(){
        return{
            inputWord: "",
            word: "",
        }
    },
    mounted(){
        document.getElementById('inputText').select();
    },
    methods: {
        submitWord() {
            if(this.inputWord != "" && this.newLetter == this.inputWord){
                this.$emit('updateWord');
                this.$emit('success');
                this.inputWord = "";
            } else {
                // this.error = "Incorrect!";
            }
        },
        randomLetters() {
            console.log('randomLetters');
            if(localStorage.arrletters) {
                let random = Math.floor(Math.random() * 102217);
                let arr = JSON.parse(localStorage.getItem('arrletters'));
                this.newLetter = arr[random];             
            }
        }
    }
}
</script>