<template>
        <button
        @click="openDialog()" 
        class="px-2 bg-green-500 rounded-md h-8 hover:bg-green-400">
            <i class="fas fa-plus"/>
            Add Event
        </button>
        <dialog ref="formDialog" class="flex flex-col rounded-md shadow-xl shadow-black bg-gray-800 border border-gray-700">
            <p class="m-3 text-center text-xl font-bold text-white">Create a New Event!</p>
            <hr class="border-gray-700" />
            <div class="flex flex-col">
                <label for="myInput" class="mx-5 mt-3 text-white">Enter Event</label>
                <input type="text" id="myInput" v-model.trim="formData.eventName"  placeholder="Enter Event" class="mx-5 rounded-md">
            </div>
            <div class="flex flex-col">
                <label for="myInput" class="mx-5  mt-3 text-white">Select a Date</label>
                <input type="date" id="myInput" v-model="formData.date"  placeholder="Enter Event" class="mx-5 rounded-md">
            </div>
            <div class="flex flex-col">
                <label for="myInput" class="mx-5  mt-3 text-white">Select a Date</label>
                <input type="time" id="myInput" v-model="formData.time"  placeholder="Enter Event" class="mx-5 rounded-md">
            </div>
            <div class="flex flex-col">
                <label for="myInput" class="mx-5  mt-3 text-white">Description</label>
                <textarea type="time" id="myInput" v-model.trim="formData.description"  placeholder="Enter Event" class="mx-5 rounded-md"/>
            </div>
            <form class="flex justify-end" method="dialog">
                <button @click="closeDialog()" class="m-5 px-2 bg-green-500 rounded-md h-8 text-black hover:bg-green-400">
                    <i class="fa-solid fa-floppy-disk"></i>
                    SAVE
                </button>
            </form>
        </dialog>
</template>

<script lang="ts">

export default{
    data(){
        return {
            formData: {
                eventName: '' as string,
                date: '' as string,
                time: '' as string,
                description: '' as string,
            },
        };
    },
    methods: {
        openDialog(){
            const dialog = this.$refs.formDialog as HTMLDialogElement;
            dialog.showModal();
        },
        closeDialog(){
            console.log(this.formData)
            const dialog = this.$refs.formDialog as HTMLDialogElement;
            dialog.close();
            this.clearData();
        },
        clearData(){
            this.formData = {
            eventName: '',
            date: '',
            time: '',
            description: '',
            };
        },
    }
}
</script>

<style>
dialog:not([open]) {
  display: none;
}
</style>