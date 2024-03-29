<script>
  import { T } from '@threlte/core'
  import { ContactShadows, Float, Grid, OrbitControls } from '@threlte/extras'
  import Boat from './models/boat.svelte'
  import { MeshBasicMaterial, PlaneGeometry, SphereGeometry } from 'three';

  /**
	 * @type {any}
	 */
  let planeRef;
  /**
	 * @type {any}
	 */
  let sphereRef;
</script>

<T.PerspectiveCamera
  makeDefault
  position={[-10, 10, 10]}
  fov={15}
>
  <OrbitControls
    enableDamping
    target={[0, 0, 0]}
  />
</T.PerspectiveCamera>

<T.DirectionalLight
  intensity={1.8}
  position={[0, 10, 0]}
  castShadow
  shadow.bias={-0.0001}
/>
<T.AmbientLight intensity={0.2} />

<Grid
  position.y={-0.001}
  cellColor="#ffffff"
  sectionColor="#ffffff"
  sectionThickness={0}
  fadeDistance={25}
  cellSize={2}
/>

<Boat />

<T.Mesh renderOrder={2} bind:ref={planeRef}>
  <T.PlaneGeometry args={[20, 20]} />
  <T.MeshBasicMaterial color={[1, 0, 1]} transparent opacity={0.25} />
</T.Mesh>

<T.Mesh position={[1, 2, 0]} bind:ref={sphereRef}>
  <T.SphereGeometry args={[1, 20, 20]} />
  <T.MeshBasicMaterial color={[1, 0, 0]} />
</T.Mesh>