<template lang="pug">
    .form-app-container
        .form-app
            .form-section
                form(@submit.prevent="submit")
                    h2.title    Student Details
                    .form
                        .form-inputs
                            input(v-model="details.name" placeholder="Enter Name")
                            input(v-model="details.mobile" placeholder="Enter Mobile")
                            input(v-model="details.email" placeholder="Enter Email")
                        button(type="submit")    Submit
            .students-data
                CustomTable(:students="students")
</template>

<script>
import CustomTable from "./components/CustomTable";
export default {
    components: { CustomTable },
    data() {
        return {
            details: {
                name: null,
                mobile: null,
                email: null
            },
            students: []
        };
    },
    watch: {
        "details.name": function(newVal) {
            console.log(`Name Changed:${newVal}`);
        }
    },
    methods: {
        submit() {
            if (
                !this.details.name ||
                !this.details.mobile ||
                !this.details.email
            ) {
                alert("All the Details Are Compulsory!");
                return;
            }

            this.students.push(this.details);
            this.reset();
        },
        reset() {
            this.details = {
                name: null,
                mobile: null,
                email: null
            };
        }
    },
    name: "App"
};
</script>

<style lang="scss">
@import "./scss/app";
.form-app-container {
    min-height: 100vh;
    background: #333;
    display: flex;
    align-items: center;
    justify-content: center;

    .form-app {
        width: 75%;
    }

    .form-section {
        border-radius: 0.8rem;
        background: #444;
        color: #fff;
        width: 100%;
        margin-bottom: 1rem;
        padding: 1rem;

        .title {
            margin-bottom: 1rem;
        }

        .form {
            text-align: center;
            .form-inputs {
                padding: 0.5rem 1rem;
                display: flex;
                justify-content: center;
            }
        }
    }
}
</style>
