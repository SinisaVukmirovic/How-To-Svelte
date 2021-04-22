<script>
    import VideoPlayer from './components/VideoPlayer.svelte';

    let y;
    // $: console.log(y);
    $: (y > 3200) ? floatVideo = true : floatVideo = false;

    let floatVideo = false;
</script>

<svelte:window bind:scrollY={y} />

<section>
    <!-- MarkUp -->
    <h2>Video Float</h2>
    <VideoPlayer {floatVideo} />
</section>

<style>

</style>