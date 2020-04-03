<template lang="pug">
    .students-data
        h2.title    Student Data
        transition(name="fade" mode="out-in" appear)
            p.message(v-if="!students.length")   Sorry, No Details Available Yet
            table(v-else)
                thead
                    tr
                        th  No
                        th Name
                        th Mobile
                        th Email
                transition-group(name="slideDown" mode="out-in" appear tag="tbody")
                    tr(v-for="(student,index) in students" :key="`Row${index}`")
                        td  {{index + 1}}
                        td  {{student.name}}
                        td      {{student.mobile}}
                        td  {{student.email}}
</template>

<script>
export default {
    props: {
        students: Array
    },
    name: "CustomTable"
};
</script>

<style lang="scss" scoped>
.students-data {
    border-radius: 0.8rem;
    background: #444;
    color: #fff;
    padding: 1rem;
    text-align: center;

    .title {
        margin-bottom: 1rem;
    }

    .message {
        font-size: 14px;
        text-transform: uppercase;
    }
}
</style>
