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
  let cube;
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
        // 相机 PerspectiveCamera(视野角度,画布宽高比,近平面,远平面)
        this.camera = new THREE.PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 100 );
        this.camera.position.set(0, 0, 10);
        this.camera.lookAt(0, 0, 0)
        // 场景
        scene = new THREE.Scene();
        // 物体形状——立方几何体
        let geometry = new THREE.BoxGeometry( 1, 1, 1 );
        // 物体材质，颜色
        let material = new THREE.MeshBasicMaterial( { color: 0x00ff00 } );
        // 场景添加物体
        cube = new THREE.Mesh(geometry, material);
        scene.add(cube);
        // 渲染器
        this.renderer = new THREE.WebGLRenderer({ antialias: true });
        this.renderer.setSize(container.clientWidth, container.clientHeight);
        container.appendChild(this.renderer.domElement);
      },
      animate() {
        requestAnimationFrame(this.animate);
        //物体旋转
        cube.rotation.x += 0.01;
        cube.rotation.y += 0.01;
        // 渲染
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