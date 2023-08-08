<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal" :class="{sale: theme === 'sale' }"  >
            <slot></slot>
            <div class="actions">
                <slot name="links"></slot>
            </div>
        </div>
    </div>
</template>

<script>
//:class="{success : theme === 'success'}"
export default {
    props: ["theme"],
    methods: {
        closeModal() {
            this.$emit("close")
        }
    }
}

</script>

<style >
    .backdrop{
        position: fixed;
        top: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, .5);
    }
    .modal{
        width: 400px;
        padding: 20px;
        border-radius: 10px;
        background: #fff;
        margin: 100px auto;
    } 
    .modal h2{
        border: none;
        padding: 0;
        color: teal;
    }
    .modal .actions {
        color: #333;
        margin: 30px 10px 0;
        text-align: center;
    }
    .modal .actions a {
        color: #333;
        border: 1px solid #eee;
        border-radius: 4px;
        margin-right: 10px;
        text-decoration: none;
        padding: 8px;
    }
    .modal.sale{
        background: crimson;
        color: #fff;
    }
    .modal .sale h2 {
        color: white;
    }
    .modal .sale .actions {
        color: white;
    }
    .modal.sale .actions a {
        color: white;
    }
    .modal.success{
        background: teal;
    }
    .modal.sale .success a{
        color: white;
    }
    .modal .success h2 {
        color: white;
    }
</style>