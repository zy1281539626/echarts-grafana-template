<template>
  <div id="app">
    <simple-graph></simple-graph>
    <smooth-data></smooth-data>
    <step-data></step-data>
    <multiple-y></multiple-y>
    <bar-gradients></bar-gradients>
    <point-data></point-data>
    <mix-style></mix-style>
    <bar-stack></bar-stack>
    <bar-histogram></bar-histogram>
  </div>
</template>

<script>
import SimpleGraph from '@/components/SimpleGraph.vue'
import SmoothData from '@/components/SmoothData.vue'
import StepData from './components/StepData.vue';
import MultipleY from './components/MultipleY.vue';
import BarGradients from './components/BarGradients.vue';
import PointData from './components/PointData.vue';
import MixStyle from './components/MixStyle.vue';
import BarStack from './components/BarStack.vue';
import BarHistogram from './components/BarHistogram.vue';

export default {
  name: 'App',
  components: {
    SimpleGraph,
    SmoothData,
    StepData,
    MultipleY,
    BarGradients,
    PointData,
    MixStyle,
    BarStack,
    BarHistogram
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
}

</style>
