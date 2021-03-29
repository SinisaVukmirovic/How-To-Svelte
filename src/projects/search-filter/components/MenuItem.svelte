<script>
    export let label;
</script>

<style>
     /* Links inside the dropdown */
    a {
    color: black;
    padding: 12px 16px;
    text-decoration: none;
    display: block;
    text-align: left;
    }

    /* Change color of dropdown links on hover */
    a:hover {background-color: #f1f1f1}
</style>

<!-- MarkUp -->
<a href="#{label.toLowerCase()}">{label}</a>