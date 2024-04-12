<script>
    import * as THREE from 'three';
    import * as SC from 'svelte-cubed';

    let spin = 0;
    SC.onFrame(() => {
        spin += 0.01;
    });
</script>

<div class="relative w-full h-[40rem]">
    <SC.Canvas 
        antialias 
        background={new THREE.Color('papayawhip')} 
        shadows
        fog={new THREE.FogExp2('papayawhip', 0.1)}
    >
        <SC.Mesh
            geometry={new THREE.BoxGeometry()}
            material={new THREE.MeshStandardMaterial({ color: 0xff3e00 })}
            rotation={[0, spin, 0]}
            castShadow
        />
        
        <SC.Group>
            <SC.Mesh
                geometry={new THREE.PlaneGeometry(50, 50)}
                material={new THREE.MeshStandardMaterial({ color: 'burlywood' })}
                rotation={[-Math.PI / 2, 0, 0]}
                receiveShadow
            />

            <SC.Primitive
                object={new THREE.GridHelper(50, 50, 0x444444, 0x555555)}
                position={[0, 0.001, 0]}
            />
        </SC.Group>
        
        <SC.PerspectiveCamera position={[1, 1, 3]} />
        <SC.OrbitControls enableZoom={false} maxPolarAngle={Math.PI * 0.51} />
        <SC.AmbientLight intensity={0.6} />
        <SC.DirectionalLight intensity={0.6} position={[-2, 3, 2]} shadow={{ mapSize: [2048, 2048] }} />
    </SC.Canvas>
    <slot/>
</div>