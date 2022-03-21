<script>

import * as THREE from "three";
import {onMounted} from "vue";

export default {
  name:"Panorama",
  setup(){

    onMounted(()=>{
      // const scene = new THREE.Scene();
      // const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );
      //
      // const renderer = new THREE.WebGLRenderer();
      // renderer.setSize( window.innerWidth, window.innerHeight );
      // document.getElementById('panoramaComponent').appendChild( renderer.domElement );
      // console.log('123123')



      const scene = new THREE.Scene();
      const camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );

      const renderer = new THREE.WebGLRenderer();
      renderer.setSize( window.innerWidth, window.innerHeight );
      document.getElementById('panoramaComponent').appendChild( renderer.domElement );

      const geometry = new THREE.BoxGeometry();
      const material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
      const cube = new THREE.Mesh( geometry, material );
      scene.add( cube );

      camera.position.z = 5;

      function animate() {
        requestAnimationFrame( animate );
        cube.rotation.x += 0.01;
        cube.rotation.y += 0.01;
        renderer.render( scene, camera );
      }
      animate()
    })
  }
}

</script>

<template>
  <main>
    <div id="panoramaComponent"/>
  </main>
</template>

<style>
@import './assets/base.css';


</style>
