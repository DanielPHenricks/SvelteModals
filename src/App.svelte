<script>
    import ButtonModal from "./lib/ButtonModal.svelte";
    import Modal from "./lib/Modal.svelte";

    const exampleContent = {
        modalTitle: "Info about Vandy Sports.",
        modalText: "These are the future sports games at Vandy: ",
    };

    const topics = ["Hey", "Baseball"];
</script>

<!-- An example of a default modal. -->
<Modal />

<!-- An example of a modal with custom content. -->
<Modal {...exampleContent} />

<ButtonModal buttonTopics={topics} />
