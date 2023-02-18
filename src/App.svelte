<script>
    import ButtonModal from "./lib/ButtonModal.svelte";
    import Modal from "./lib/Modal.svelte";

    const exampleContent = {
        modalTitle: "Info about Vandy Sports.",
        modalText: "These are the future sports games at Vandy: ",
    };

    const topics = [
        "Baseball",
        "Men's Basketball",
        "Women's Basketball",
        "Swimming",
        "Football",
    ];
</script>

<!-- An example of a modal with custom content. -->
<Modal {...exampleContent} />

<!-- An example of a modal to save user preferences. -->
<ButtonModal buttonTopics={topics} />

<!-- Example usage of the ButtonModal class-->
<p>Topics I'm interested in:</p>
{JSON.parse(localStorage.getItem("prefs"))}
