<template>
    <div class="container">

        <section>

            <b-field group-multiline grouped>
                <div class="control">
                    <b-switch v-model="showDetailIcon">Show detail icon</b-switch>
                </div>
            </b-field>

            <b-table
                    :data="data"
                    :opened-detailed="defaultOpenedDetails"
                    :show-detail-icon="showDetailIcon"
                    @details-open="(row, index) => $buefy.toast.open(`Expanded ${row.user.first_name}`)"
                    aria-current-label="Current page"
                    aria-next-label="Next page"
                    aria-page-label="Page"
                    aria-previous-label="Previous page"
                    detail-key="id"
                    detailed
                    paginated
                    per-page="5"
                    ref="table">

                <template slot-scope="props">
                    <b-table-column field="user.first_name" label="Vorname" sortable>
                        <template v-if="showDetailIcon">
                            {{ props.row.user.first_name }}
                        </template>
                        <template v-else>
                            <a @click="toggle(props.row)">
                                {{ props.row.user.first_name }}
                            </a>
                        </template>
                    </b-table-column>

                    <b-table-column field="user.last_name" label="Nachname" sortable>
                        {{ props.row.user.last_name }}
                    </b-table-column>

                    <b-table-column field="user.value" label="value" sortable>
                        {{ props.row.value }}
                    </b-table-column>

                    <b-table-column centered field="user.value" label="Feedback" sortable>
                        <FeedbackSlider v-bind:value="props.row.value"/>
                    </b-table-column>

                    <b-table-column centered field="date" label="Aktualisierung" sortable>
                        <span class="tag is-success">
                            {{ new Date(props.row.date).toLocaleDateString() }}
                        </span>
                    </b-table-column>


                </template>

                <template slot="detail" slot-scope="props">
                    <article class="media">
                        <figure class="media-left">
                            <p class="image is-64x64">
                                <img src="https://buefy.org/static/img/placeholder-128x128.png">
                            </p>
                        </figure>
                        <div class="media-content">
                            <div class="content">
                                <p>
                                    <strong>{{ props.row.user.first_name }} {{ props.row.user.last_name }}</strong>
                                    <small>@{{ props.row.user.first_name }}</small>
                                    <small>31m</small>
                                    <br>
                                    Lorem ipsum dolor sit amet, consectetur adipiscing elit.
                                    Proin ornare magna eros, eu pellentesque tortor vestibulum ut.
                                    Maecenas non massa sem. Etiam finibus odio quis feugiat facilisis.
                                </p>
                            </div>
                        </div>
                    </article>
                </template>
            </b-table>

        </section>

    </div>
</template>

<script>
  import Vue from 'vue'
  import Table from 'buefy'
  import 'buefy/dist/buefy.css'
  import FeedbackSlider from "@/components/FeedbackSlider";

  Vue.use(Table);
  export default {
    name: "FeedbackTable",
    components: {FeedbackSlider},
    data() {
return {
data,
defaultOpenedDetails: [1],
showDetailIcon: true
}
},
methods: {
toggle(row) {
this.$refs.table.toggleDetails(row)
},

sliderChange: function(value) {
alert(value)
}

}
}
const data = [{
"id": 1,
"user": {"first_name": "Jesse", "last_name": "Simmons"},
"date": "2016/10/15 13:43:27",
"value": "3"
},
{"id": 2, "user": {"first_name": "John", "last_name": "Jacobs"}, "date": "2016/12/15 06:00:53", "value": "3"},
{
"id": 3,
"user": {"first_name": "Tina", "last_name": "Gilbert"},
"date": "2016/04/26 06:26:28",
"value": "8"
},
{
"id": 4,
"user": {"first_name": "Clarence", "last_name": "Flores"},
"date": "2016/04/10 10:28:46",
"value": "3"
},
{"id": 5, "user": {"first_name": "Anne", "last_name": "Lee"}, "date": "2016/12/06 14:38:38", "value": "8"},
{
"id": 6,
"user": {"first_name": "Sara", "last_name": "Armstrong"},
"date": "2016/09/23 18:50:04",
"value": "8"
},
{"id": 7, "user": {"first_name": "Anthony", "last_name": "Webb"}, "date": "2016/08/30 23:49:38", "value": "3"},
{"id": 8, "user": {"first_name": "Andrew", "last_name": "Greene"}, "date": "2016/11/20 14:57:47", "value": "3"},
{"id": 9, "user": {"first_name": "Russell", "last_name": "White"}, "date": "2016/07/13 09:29:49", "value": "3"},
{
"id": 10,
"user": {"first_name": "Lori", "last_name": "Hunter"},
"date": "2016/12/09 01:44:05",
"value": "8"
},
{"id": 11, "user": {"first_name": "Ronald", "last_name": "Wood"}, "date": "2016/12/04 02:23:48", "value": "3"},
{
"id": 12,
"user": {"first_name": "Michael", "last_name": "Harper"},
"date": "2016/07/27 13:28:15",
"value": "3"
},
{"id": 13, "user": {"first_name": "George", "last_name": "Dunn"}, "date": "2017/03/07 12:26:52", "value": "3"},
{"id": 14, "user": {"first_name": "Eric", "last_name": "Rogers"}, "date": "2016/06/07 05:41:52", "value": "3"},
{"id": 15, "user": {"first_name": "Juan", "last_name": "Meyer"}, "date": "2017/02/01 04:56:34", "value": "3"},
{"id": 16, "user": {"first_name": "Lori", "last_name": "Shaw"}, "date": "2017/01/26 11:50:04", "value": "8"},
{
"id": 17,
"user": {"first_name": "Lori", "last_name": "Cunningham"},
"date": "2016/05/01 10:00:56",
"value": "8"
},
{
"id": 18,
"user": {"first_name": "Charles", "last_name": "Graham"},
"date": "2016/05/31 06:43:30",
"value": "3"
},
{
"id": 19,
"user": {"first_name": "Henry", "last_name": "Morrison"},
"date": "2016/09/27 16:15:44",
"value": "3"
},
{
"id": 20,
"user": {"first_name": "Albert", "last_name": "Mendoza"},
"date": "2016/08/08 05:29:24",
"value": "3"
},
{
"id": 21,
"user": {"first_name": "Ruby", "last_name": "Snyder"},
"date": "2017/04/01 12:04:39",
"value": "8"
},
{"id": 22, "user": {"first_name": "Jesse", "last_name": "Warren"}, "date": "2016/08/20 01:36:38", "value": "3"},
{
"id": 23,
"user": {"first_name": "Carlos", "last_name": "Ferguson"},
"date": "2016/05/31 10:40:29",
"value": "3"
},
{
"id": 24,
"user": {"first_name": "Melissa", "last_name": "Peters"},
"date": "2016/07/23 00:41:54",
"value": "8"
},
{"id": 25, "user": {"first_name": "Arthur", "last_name": "Garza"}, "date": "2017/03/11 14:11:37", "value": "3"},
{"id": 26, "user": {"first_name": "Joe", "last_name": "Berry"}, "date": "2016/07/09 15:16:56", "value": "3"},
{
"id": 27,
"user": {"first_name": "Joseph", "last_name": "Bishop"},
"date": "2016/10/04 19:44:54",
"value": "3"
},
{
"id": 28,
"user": {"first_name": "Sarah", "last_name": "Harper"},
"date": "2016/09/23 05:09:11",
"value": "8"
},
{
"id": 29,
"user": {"first_name": "Christopher", "last_name": "Fuller"},
"date": "2016/04/12 00:05:35",
"value": "3"
},
{"id": 30, "user": {"first_name": "Alan", "last_name": "Mendoza"}, "date": "2016/04/22 10:48:02", "value": "3"},
{"id": 31, "user": {"first_name": "James", "last_name": "Davis"}, "date": "2017/01/16 15:17:03", "value": "3"},
{"id": 32, "user": {"first_name": "Scott", "last_name": "Welch"}, "date": "2016/10/04 23:31:51", "value": "3"},
{
"id": 33,
"user": {"first_name": "Mildred", "last_name": "Myers"},
"date": "2016/11/23 13:46:18",
"value": "8"
},
{
"id": 34,
"user": {"first_name": "Victor", "last_name": "Martinez"},
"date": "2016/04/06 17:05:07",
"value": "3"
},
{
"id": 35,
"user": {"first_name": "Susan", "last_name": "Medina"},
"date": "2016/12/09 10:33:37",
"value": "8"
},
{"id": 36, "user": {"first_name": "Judy", "last_name": "Long"}, "date": "2016/07/26 16:19:04", "value": "8"},
{"id": 37, "user": {"first_name": "Joan", "last_name": "Myers"}, "date": "2016/09/22 04:55:54", "value": "8"},
{
"id": 38,
"user": {"first_name": "Rachel", "last_name": "Gonzales"},
"date": "2016/07/15 13:56:38",
"value": "8"
},
{"id": 39, "user": {"first_name": "Roger", "last_name": "Hunt"}, "date": "2016/08/14 10:43:11", "value": "3"},
{
"id": 40,
"user": {"first_name": "Dorothy", "last_name": "Howard"},
"date": "2016/06/19 05:34:49",
"value": "8"
},
{"id": 41, "user": {"first_name": "Eugene", "last_name": "Lynch"}, "date": "2016/12/24 08:19:24", "value": "3"},
{"id": 42, "user": {"first_name": "Kathy", "last_name": "Webb"}, "date": "2017/04/01 21:09:05", "value": "8"},
{
"id": 43,
"user": {"first_name": "Antonio", "last_name": "White"},
"date": "2017/02/10 06:51:20",
"value": "3"
},
{
"id": 44,
"user": {"first_name": "Louis", "last_name": "Spencer"},
"date": "2016/10/08 02:20:22",
"value": "3"
},
{
"id": 45,
"user": {"first_name": "Andrea", "last_name": "Marshall"},
"date": "2016/09/04 10:59:57",
"value": "8"
},
{"id": 46, "user": {"first_name": "Eugene", "last_name": "Sims"}, "date": "2017/03/15 06:39:48", "value": "3"},
{
"id": 47,
"user": {"first_name": "Mildred", "last_name": "Gibson"},
"date": "2016/04/18 06:43:54",
"value": "8"
},
{
"id": 48,
"user": {"first_name": "Joan", "last_name": "Arnold"},
"date": "2016/12/16 04:52:23",
"value": "8"
},
{
"id": 49,
"user": {"first_name": "Jesse", "last_name": "Schmidt"},
"date": "2016/06/11 02:44:33",
"value": "3"
},
{
"id": 50,
"user": {"first_name": "David", "last_name": "Frazier"},
"date": "2017/02/15 21:46:30",
"value": "3"
},
{
"id": 51,
"user": {"first_name": "Nicholas", "last_name": "Howell"},
"date": "2016/11/01 15:08:31",
"value": "3"
},
{
"id": 52,
"user": {"first_name": "Douglas", "last_name": "Chapman"},
"date": "2017/02/08 03:33:24",
"value": "3"
},
{
"id": 53,
"user": {"first_name": "Bruce", "last_name": "Simmons"},
"date": "2016/07/14 12:11:17",
"value": "3"
},
{
"id": 54,
"user": {"first_name": "Antonio", "last_name": "George"},
"date": "2016/11/07 19:12:55",
"value": "3"
},
{
"id": 55,
"user": {"first_name": "Chris", "last_name": "Marshall"},
"date": "2016/07/03 12:11:45",
"value": "3"
},
{
"id": 56,
"user": {"first_name": "Ashley", "last_name": "Hudson"},
"date": "2016/10/14 21:08:05",
"value": "8"
},
{"id": 57, "user": {"first_name": "Alan", "last_name": "Edwards"}, "date": "2017/03/22 21:10:25", "value": "3"},
{"id": 58, "user": {"first_name": "George", "last_name": "Clark"}, "date": "2016/04/28 03:15:05", "value": "3"},
{"id": 59, "user": {"first_name": "Frank", "last_name": "Porter"}, "date": "2016/09/08 00:48:14", "value": "3"},
{
"id": 60,
"user": {"first_name": "Christopher", "last_name": "Palmer"},
"date": "2016/05/24 08:58:12",
"value": "3"
}]
</script>
<style scoped>

</style>
