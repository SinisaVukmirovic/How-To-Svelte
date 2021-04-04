<script>
    import { images } from '../slideshow-gallery/data/images';
</script>

<!-- MarkUp -->
<div class="demo-img">
    {#each images as { id, imgUrl, name }}
        <div class="demo-container">
            <img {id} src={imgUrl} alt={name} on:click />
        </div>
    {/each}
</div>

<style>
    .demo-img {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }
    .demo-container {
        width: 33%;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    img {
        width: 90%;
        margin: 10px 0;
        border: 4px solid #ccc;
        transition: box-shadow .3s linear;
        cursor: pointer;
    }
        img:hover {
            box-shadow: 1px 1px 20px #000;
        }
</style>