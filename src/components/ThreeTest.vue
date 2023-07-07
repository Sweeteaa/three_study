<template>
  <div>
    <div id="container"></div>
  </div>
</template>

<script>
  import * as THREE from "three";
  // 场景和物体不能放在data初始化
  let scene;
  // let mesh;
  // let cube;
  let points = [];
  export default {
    name: "THREETest",
    data() {
      return {
        camera: null,
        renderer: null,
      };
    },
    methods: {
      init() {
        let container = document.getElementById("container");
        // 相机
        this.camera = new THREE.PerspectiveCamera( 45, window.innerWidth / window.innerHeight, 1, 500 );
        this.camera.position.set(0, 0, 100);
        this.camera.lookAt(0, 0, 0)
        // 场景
        scene = new THREE.Scene();
        // 物体形状
        // let geometry = new THREE.BoxGeometry( 1, 1, 1 );
        points.push( new THREE.Vector3( - 10, 0, 0 ) );
        points.push( new THREE.Vector3( 0, 10, 0 ) );
        points.push( new THREE.Vector3( 10, 0, 0 ) );

        let geometry = new THREE.BufferGeometry().setFromPoints( points );
        // let material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
        // 物体线条材质
        let material = new THREE.LineBasicMaterial( { color: 0x0000ff } );
        // 场景添加物体
        // cube = new THREE.Mesh(geometry, material);
        let cube = new THREE.Line( geometry, material );
        scene.add(cube);
        // 渲染器
        this.renderer = new THREE.WebGLRenderer({ antialias: true });
        this.renderer.setSize(container.clientWidth, container.clientHeight);
        container.appendChild(this.renderer.domElement);
      },
      animate() {
        requestAnimationFrame(this.animate);
        // cube.rotation.x += 0.01;
        // cube.rotation.y += 0.01;
        this.renderer.render(scene, this.camera);
      },
    },
    mounted() {
      this.init();
      this.animate();
    },
  };
</script>

<style scoped>

  #container {
    height: 400px;
  }

</style>