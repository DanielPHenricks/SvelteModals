<script>
  // Whether the modal should be shown or not.
  let showModal = false;

  // What the default button title should be.
  const buttonTitle = "Open";

  // The title for the modal.
  export let modalTitle = "Title";

  // The text in the middle of the modal.
  export let modalText = "Body";
</script>

<button on:click={() => (showModal = true)}>{buttonTitle}</button>

{#if showModal}
  <div class="modal-overlay">
    <div class="modal-content">
      <h3>{modalTitle}</h3>
      <p>{modalText}</p>
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
    background-color: white;
    padding: 1rem;
    border-radius: 4px;
  }
</style>
