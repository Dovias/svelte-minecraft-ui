<script context="module" lang="ts">
	export type PanoramaProps = {
			speed?: number;
	}
</script>

<script lang="ts">
	import { onMount } from 'svelte';
	import * as THREE from 'three';

	export let speed: NonNullable<PanoramaProps['speed']> = 0.0005;

	let canvas: HTMLCanvasElement;

	onMount(() => {
		const scene = new THREE.Scene();
		const camera = new THREE.PerspectiveCamera(90, canvas.clientWidth / canvas.clientHeight);
		const renderer = new THREE.WebGLRenderer({canvas});

		renderer.setSize(canvas.clientWidth, canvas.clientHeight, false);
		renderer.setPixelRatio(window.devicePixelRatio);

		const skyboxLoader = new THREE.CubeTextureLoader();
		skyboxLoader.setPath('/panorama/');

		scene.background = skyboxLoader.load([
			'right.png',
			'left.png',
			'top.png',
			'bottom.png',
			'front.png',
			'back.png'
    ]);

		// create a container for the camera in order to ignore tilt
		const cameraContainer = new THREE.Object3D();
		scene.add(cameraContainer);
		cameraContainer.add(camera);

		// tilt the camera and rotate it back to match minecraft's panorama starting point
		camera.rotation.x = THREE.MathUtils.degToRad(20);
		camera.rotation.y = THREE.MathUtils.degToRad(-180);

		function onWindowResize() {
			const canvas = renderer.domElement;
			// look up the size the canvas is being displayed
			const width = canvas.clientWidth;
			const height = canvas.clientHeight;

			renderer.setSize(width, height, false);
			camera.aspect = width / height;
			camera.updateProjectionMatrix();
    	}

		function animate() {
			window.requestAnimationFrame(animate);

			cameraContainer.rotateY(speed);
			renderer.render(scene, camera);
		}

		animate();

		window.addEventListener('resize', onWindowResize);
		return () => window.removeEventListener('resize', onWindowResize);
	});

</script>

<canvas bind:this={canvas} class="panorama" />

<style>
	.panorama {
		display: block;
		position: absolute;

		width: 100%;
		height: 100%;

	}
</style>