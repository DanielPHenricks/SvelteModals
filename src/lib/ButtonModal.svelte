<script>
    // Whether the modal should be shown or not.
    let showModal = false;

    // What the default button title should be.
    const buttonTitle = "Preferences";

    // The title for the modal.
    export let modalTitle = "Set Preferences";

    // The text in the middle of the modal.
    export let buttonTopics = [];

    // By default, there are no prefs.
    let hasSavedPrefs = false;

    // The saved preferences.
    let savedPrefs = [];

    // When the submit button is clicked.
    const processButtonClick = () => {
        const form = document.querySelector("#buttonForm");
        const checked = form.querySelectorAll('input[type="checkbox"]:checked');
        let labels = [];
        checked.forEach((box) => {
            const label = form.querySelector('label[for="' + box.id + '"]');
            labels.push(label.innerHTML);
        });
        const string = JSON.stringify(labels);
        localStorage.setItem("prefs", string);
    };

    // Load the saved prefs.
    const openModal = () => {
        showModal = true;
        const str = localStorage.getItem("prefs");
        if (str != undefined) {
            const parsed = JSON.parse(str);
            modalTitle = "Saved Preferences";
            hasSavedPrefs = true;
            buttonTopics = parsed;
        }
    };
</script>

<button on:click={() => openModal()}>{buttonTitle}</button>

{#if showModal}
    <div class="modal-overlay">
        <div class="modal-content dark-mode">
            <h3>{modalTitle}</h3>
            <form id="buttonForm">
                <div class="text-left">
                    {#each buttonTopics as topic}
                        <input
                            class="form-check-input mt-2"
                            type="checkbox"
                            value=""
                            id="defaultCheck{topic}"
                        />
                        <label
                            class="form-check-label"
                            for="defaultCheck{topic}"
                        >
                            {topic}
                        </label>
                        <br />
                    {/each}
                </div>
                <button
                    type="submit"
                    class="btn btn-primary m-3"
                    on:click={() => processButtonClick()}>Submit</button
                >
            </form>
            <button
                on:click={() => {
                    showModal = false;
                }}>Close</button
            >
        </div>
    </div>
{/if}

<style>
    .modal-overlay {
        position: fixed;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        background-color: rgba(0, 0, 0, 0.5);
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .modal-content {
        max-width: 30vw;
        padding: 1rem;
        border-radius: 4px;
        justify-content: center;
    }

    .dark-mode {
        background-color: black;
        color: white;
    }

    .text-left {
        text-align: left;
    }

    label {
        display: inline-block;
    }
</style>
