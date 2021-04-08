<script>

</script>

<!-- MarkUp -->
<!-- Portfolio Gallery Grid -->
<div class="row">
    <slot></slot>
</div>


<style>
    .row {
      margin: 8px -16px;
    }

    /* Add padding BETWEEN each column (if you want) */
    /* .row,
    .row > .column {
    padding: 8px;
    } */

    /* Clear floats after rows */
    .row:after {
    content: "";
    display: table;
    clear: both;
    }
</style>