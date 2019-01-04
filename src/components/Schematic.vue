<template>
  <div>
    <h2>{{msg}}</h2>

    <div class="wrp">
      <div class="dragDrop">
        <h3>drag&drop zone</h3>
        <div v-for="(block,index) in blockList" :key="index" class="bWrp draggable">
          <Block
            :blockName="block.blockName"
            :blockInfo="block.blockInfo"
          >
            <span class="pinDraggable">
                <strong class="flexBox" @mouseup="draw()">+</strong>
            </span>
          </Block>
        </div>

      </div>

    </div>


  </div>
</template>

<script>
  import Block from './Block.vue'

  /* ------ drag and drop ------ */
  import interact from 'interactjs'
  // target elements with the "draggable" class
  interact('.draggable,.pinDraggable')
          .draggable({
            // enable inertial throwing
            inertia: true,
            // keep the element within the area of it's parent
            restrict: {
              restriction: "parent",
              endOnly: true,
              elementRect: { top: 0, left: 0, bottom: 1, right: 1 }
            },
            // enable autoScroll
            autoScroll: true,

            // call this function on every dragmove event
            onmove: dragMoveListener,
            // call this function on every dragend event
            onend: function () {
              //do nothing

            }
          });


  function dragMoveListener (event) {
    var target = event.target,
            // keep the dragged position in the data-x/data-y attributes
            x = (parseFloat(target.getAttribute('data-x')) || 0) + event.dx,
            y = (parseFloat(target.getAttribute('data-y')) || 0) + event.dy;
    //console.log(`x is ${x}   y is  ${y}`);

    // translate the element
    target.style.webkitTransform =
            target.style.transform =
                    'translate(' + x + 'px, ' + y + 'px)';

    // update the posiion attributes
    target.setAttribute('data-x', x);
    target.setAttribute('data-y', y);
  }

  // this is used later in the resizing and gesture demos
  window.dragMoveListener = dragMoveListener;

  /* ------ end of drag and drop ------ */

export default {
  name: 'Schematic',
  data:()=>{
    return {
      blockList:[
        {
          blockName:'first Block',
          blockInfo:'some information',
          coord:[0,0]
        },
        {
          blockName:'second Block',
          blockInfo:'another information',
          coord:[0,0]
        }
      ],
      pinCoord:{
        start:[0,0],
        end:[0,0]
      },
      drawStarted:false
    };
  },
  props: {
    msg: String
  },
  components: {
    Block
  },
  methods: {
    draw(){
      //console.log(this.drawStarted);
      if(!this.drawStarted)  {
        this.startDraw();
        return;
      }
      this.finishDraw();

    },
    startDraw() {
      this.drawStarted = true;
      alert("line drawing must be start");
    },
    finishDraw() {
      this.drawStarted = false;
      alert("line drawing must be finish");
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  div.wrp {
    display: flex;
    flex-wrap: wrap;
  }
  div.dragDrop {
    display: block;
    margin: 0 auto;
    min-height: 30rem;
    width: 70%;
    background-color: burlywood;
    padding: .5rem;
  }
  .bWrp {
    display: inline-block;
  }
</style>
