<template>
  <div>sss</div>
  <div ref="container" class="container"></div>
</template>

<script lang="ts" setup>
import { onMounted, ref } from 'vue';
import * as THREE from 'three';
// import { Scene } from 'three';

// const scene = new Scene();

const container = ref()

const scene = new THREE.Scene();

const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000 )
const renderer = new THREE.WebGLRenderer();
renderer.setSize( window.innerWidth/1.2, window.innerHeight/1.2 );

const geometry = new THREE.BoxGeometry( 1, 1, 1 );
const material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
const cube = new THREE.Mesh( geometry, material );
scene.add( cube );

camera.position.z = 5;

function animate() {
	requestAnimationFrame( animate );
	renderer.render( scene, camera );
}


// scene.init(container)

onMounted(() => {
  container.value.appendChild(renderer.domElement);
  animate();
})

</script>

<style lang="less" scoped>

</style>