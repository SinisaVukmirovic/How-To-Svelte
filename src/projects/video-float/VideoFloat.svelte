<script>
    import VideoPlayer from './components/VideoPlayer.svelte';

    let y;
    // $: console.log(y);
    $: (y > 2500) ? floatVideo = true : floatVideo = false;

    let floatVideo = false;
</script>

<svelte:window bind:scrollY={y} />

<!-- MarkUp -->
<h2>Video Float</h2>
<VideoPlayer {floatVideo} />

<style>

</style>