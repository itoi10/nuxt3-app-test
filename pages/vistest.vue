<template>
  <div>
    <button @click="visSetup">リセット</button>
    <div id="network"></div>
  </div>
</template>

<script setup>

import { DataSet } from 'vis-data';
import { Network } from 'vis-network';

const visSetup = () => {
  const nodes = new DataSet([
    { id: 1, label: 'マサラタウン', shape: 'circle' },
    { id: 2, label: 'トキワシティ', shape: 'circle' },
    { id: 3, label: 'ニビシティ', shape: 'circle' },
    { id: 4, label: 'ハナダシティ', shape: 'circle' },
    { id: 5, label: 'ヤマブキシティ', shape: 'circle' },
    { id: 6, label: 'クチバシティ', shape: 'circle' },
    { id: 7, label: 'シオンタウン', shape: 'circle' },
    { id: 8, label: 'タマムシシティ', shape: 'circle' },
    { id: 9, label: ' ', shape: 'circle' },
    { id: 10, label: 'セキチクシティ', shape: 'circle' },
    { id: 11, label: 'グレンタウン', shape: 'circle' },
    { id: 12, label: 'セキエイこうげん', shape: 'circle' },
  ]);
  const edges = new DataSet([
    { from: 1, to: 2 },
    { from: 2, to: 3 },
    { from: 2, to: 12 },
    { from: 3, to: 4 },
    { from: 4, to: 5 },
    { from: 5, to: 6 },
    { from: 6, to: 9 },
    { from: 5, to: 7 },
    { from: 5, to: 8 },
    { from: 8, to: 10 },
    { from: 7, to: 9 },
    { from: 4, to: 7 },
    { from: 9, to: 10 },
    { from: 10, to: 11 },
    { from: 11, to: 1 },
  ]);
  const container = document.getElementById('network');
  const data = {
    nodes: nodes,
    edges: edges
  };
  const options = {
    width: '100%',
    height: '100%',
  };
  new Network(container, data, options);
}

</script>

<style scoped>
#network {
  width: 100%;
  height: 100vh;
}
</style>
