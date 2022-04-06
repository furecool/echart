<template>
  <div class="demo">
    
    <div id="radar-chart" style="border: 1px solid black; width: 800px; height: 600px; margin: 5px;">
        <radar-chart/>
    </div>

  </div>
</template>
<script>
import radarChart from '@/components/radar-chart';
export default {
    name: 'radar-chart-demo',
    components: {
        radarChart,
    },
};
</script>