<template lang="html">

  <section class="nested-list">
    <div :id="id"></div>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'NestedList',
    props: {
      id: {
        type: String
      },
      dataList: {
        type: Object
      }
    },
    mounted () {
      this.nestedList();
    },
    data () {
      return {

      }
    },
    methods: {
      nestedList: function () {
        var array = ["<ul>"];

        function printList(items) {

          switch (Object.prototype.toString.call(items).replace(/^\[object (.+)\]$/, '$1').toLowerCase()) {

            case "object":

              getChildren(items);
              break;

            case "string":

              array.push("<li>" + items + "</li>");
              break;

            case "array":

              printArray(items);
              break;

          }

        }

        function getChildren(parent) {

          for (var child in parent) {
              
            array.push("<li>" + child + "<ul>");
            printList(parent[child]);
            array.push("</ul></li>");

          }

        }

        function printArray(myArray){

          for(var i = 0; i < myArray.length; i++){

            array.push("<li>" + myArray[i] + "</li>");

          }

        }

        printList(this.dataList);

        array.push("<ul>");

        document.getElementById(this.id).innerHTML = array.join("");

      }
    },
    computed: {

    }
}


</script>

<style scoped lang="scss">
  .nested-list {

  }
</style>
