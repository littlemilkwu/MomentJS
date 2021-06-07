<template lang='pug'>
.calender
    .container
        .calender--top
            .calender__view {{now}} ({{nowDay}})
        .calender--bottom
            .calender__edit__block
                .up(@click="increase('years')")
                .calender__edit__value {{ mom.format('YYYY') }}年
                .down(@click="decrease('years')")
            .calender__edit__block
                .up(@click="increase('months')")
                .calender__edit__value {{ mom.format('MM') }}月
                .down(@click="decrease('months')")
            .calender__edit__block
                .up(@click="increase('days')")
                .calender__edit__value {{ mom.format('DD') }}日
                .down(@click="decrease('days')")
</template>
<script>
import moment from 'moment'
export default {
    data () {
        return {
           'mom': moment()
        }
    },
    computed: {
        'now': function () {
            return this.mom.format("YYYY-MM-DD")
        },
        'nowDay': function () {
            let chiDay = {
                'Monday': "一",
                'Tuesday': '二',
                'Wednesday': "三",
                'Thursday': "四",
                'Friday': '五'
            }
            let output = chiDay[this.mom.format("dddd")]
            return output
        }
    },
    methods: {
        increase: function (time) {
            // this.mom = this.mom.add(1, time).calendar()
            console.log(this.mom)
            this.mom.add(1, time)
            console.log(this.mom)
        }
    }
}
</script>
<style lang="sass" scoped>
.calender
    margin-top: 20px
    display: flex
    justify-content: center
.container
    width: 500px
    display: flex
    flex-direction: column
.calender--top
    padding: 20px
    font-size: 2rem
.calender--bottom
    display: flex
    .calender__edit__block
        flex: 1 1 auto

        display: flex
        flex-direction: column
        align-items: center
        font-size: 1.2rem
        .up
            width: 0
            height: 0
            border-color: transparent transparent black transparent
            border-style: solid
            border-width: 0 20px 20px 20px
            cursor: pointer
        .down
            width: 0
            height: 0
            border-color: black transparent transparent transparent
            border-style: solid
            border-width: 20px 20px 0 20px
            cursor: pointer
        .calender__edit__value
            margin: 10px 0 10px 0
</style>