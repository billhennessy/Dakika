<template>
    <div class="item item-minute " v-bind:class="minute.incomplete? activeClass:'',errorClass"
         style="padding-top: 0.2em !important; padding-bottom: 0.2em !important;padding-left: 0.3em;">

        <div class="content" style="cursor: pointer">
            <div class="description" v-on:click="editItem(minute)" style="padding-right: 2px !important;">
                <p class="minute-text">{{minute.modified_minute}}</p>
            </div>
            <div class="extra noselect" style="padding-right: 2px;">
                <div class="ui  green label">
                    <i class="white clock icon"></i>{{minute.time}}

                </div>
                &nbsp;&nbsp;<a class="ui teal  label" v-if="minute.agenda"> <i class="tasks icon"></i> {{minute.agenda}}</a>
                <a class="ui teal image label" v-for="person in minute.people">
                    <img src="jenny.jpg">
                    {{person}}

                </a>

                &nbsp;&nbsp;

                <div v-for="tag in minute.tags" class="ui violet  label">
                    <i class="briefcase icon"></i>
                    {{tag.replace('#', "")}}


                </div>

                <div class="mini  ui icon button red right floated " v-on:click="deleteItem(minute)"
                     style=" cursor: pointer">
                    <i class="remove icon "> </i> Delete


                </div>
                <div data-tooltip="Insert minute After" class="mini circular ui icon button purple right floated "
                     style="cursor: pointer">
                    <i class="angle double up icon " v-on:click="addItemAfter(minute)"> </i>


                </div>
            </div>
        </div>
    </div>
</template>

<script>
  export default {
    props: ['minute'],
    data: function () {
      return {
        activeClass: 'incomplete',
        errorClass: ''
      }
    },
    methods: {
      deleteItem: function (item) {
        this.$emit('delete-item', item)
      },
      editItem: function (item) {
        this.$emit('edit-item', item)
      },
      addItemAfter: function (item) {
        this.$emit('add-item-after', item)
      }
    }
  }
</script>

<style>
    .incomplete {
        background: rgba(214, 3, 3, 0.6) !important;
    }

</style>
