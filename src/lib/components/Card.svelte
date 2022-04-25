<script lang="ts">
    export let width: string = "auto";
</script>

<div {width}>
    <slot></slot>
</div>

<style>
    div {
        border-radius: 6px;
        padding: 50px;
        margin: 25px 0;
        height: auto;
        background-color: #F4FEFF;
        box-shadow: 0 10px 20px rgba(67, 4, 214, 0.062);

        transition: transform 0.5s;
    }

    div:hover {
        transform: scale(1.01);
    }


</style>