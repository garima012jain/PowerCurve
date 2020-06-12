<!-- Finding token of first person in queue (firsttoken)
Applying firsttoken -= firsttoken%20; -->
<template>
  <div id="app">
    <line-chart :data="graph"></line-chart>
    <!--<button @click="updateChart">Click to update data</button>-->
  </div>
</template>

<script>
import firebase from "firebase";
export default {
  name: "App",
  data() {
    return {
      queue: [
        [1, 2],
        [2, 10],
        [5, 21],
        [6, 41],
        [8, 61],
        [10, 82]
      ],
      graph: []
      /*         ["0-10", 1],
        ["10-20", 1],
        ["20-30", 5],
        ["30-40", 3],
        ["40-50", 4] */
    };
  },
  methods: {
    makegraph: function() {
      let dbref = firebase.database().ref();
      console.log("hi");
      dbref.child("queue").on("value", snap => {
        console.log(snap);
        /*var firsttoken;
        snap.forEach(function(child) {
          firsttoken = child.val();
          return;
        });
        //queuelength = snap.numChildren();
        var range = 20;
        //var range = Math.ceil(queuelength / 15);
        firsttoken = firsttoken - (firsttoken % range);
        var counter = 0;
        var multi = firsttoken / range + 1;
        var l;
        var r;
        var left;
        var right;
        var key;
        var value;
        snap.forEach(function(child) {
          if (child.val <= range * multi) counter++;
          else {
            var l = range * multi;
            var r = range * (multi - 1);
            var left = l.toString();
            var right = r.toString();
            var key = left + "-" + right;
            var value = range - counter;
            var pair = [];
            pair.push(key);
            pair.push(value);
            this.graph.push(pair);
            counter = 0;
            multi++;
            while (child.val > multi * range) {
              l = range * multi;
              r = range * (multi - 1);
              left = l.toString();
              right = r.toString();
              value = range - counter;
              key = left + "-" + right;
              var pair1 = [];
              pair1.push(key);
              pair1.push(value);
              this.graph.push(pair1);
              multi++;
            }
            counter = 1;
          }
        });
        l = range * multi;
        r = range * (multi - 1);
        left = l.toString();
        right = r.toString();
        key = left + "-" + right;
        value = range - counter;
        var pair2 = [];
        pair2.push(key);
        pair2.push(value);
        this.graph.push(pair2);*/
      });
    }

    /*     updateChart() {
      this.graph = [
        ["0-10", 2],
        ["10-20", 7],
        ["20-30", 5],
        ["30-40", 3],
        ["40-50", 4]
      ];
    } */
  },
  mounted() {
    console.log("hi");
    this.makegraph();
  }
};
</script>


<style>
#app {
  align-content: center;
}
</style>
