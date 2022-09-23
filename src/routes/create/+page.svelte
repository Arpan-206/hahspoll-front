<script>
  let resJ;
  async function createPoll(e) {
    const formData = new FormData(e.target);

    const data = {};
      const res = await fetch(
        "https://24yl4zi1hh.execute-api.us-east-1.amazonaws.com/create",
        {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify({
            question: formData.get("question"),
            option1: formData.get("option1"),
            option2: formData.get("option2"),
            option3: formData.get("option3"),
            option4: formData.get("option4"),
          }),
        }
      );
      if (res.ok) {
        resJ = await res.json();
        resJ = resJ.poll;
        openDialog();
      } else {
        alert("Error creating poll");
      }
  }
  function openDialog() {
    const dialog = document.querySelector("dialog");
    dialog.open = true;
  }

  function closeDialog() {
    const dialog = document.querySelector("dialog");
    dialog.open = false;
  }
  function formRedirect() {
    window.location.href = "/vote/" + resJ.id;
  }
</script>

<svelte:head>
  <title>Create | Hashpoll</title>
  <meta name="description" content="Hash Poll" />
</svelte:head>

<main>
  <h1>Create a Poll</h1>

  <form on:submit|preventDefault={createPoll}>
    <label for="question">Question</label>
    <input
      type="text"
      name="question"
      id="question"
      placeholder="What is your favorite color?"
      required
    />
    <label for="option1">Option 1</label>
    <input type="text" name="option1" id="option1" placeholder="Red" required />
    <label for="option2">Option 2</label>
    <input
      type="text"
      name="option2"
      id="option2"
      placeholder="Blue"
      required
    />
    <label for="option3">Option 3</label>
    <input
      type="text"
      name="option3"
      id="option3"
      placeholder="Green"
      required
    />
    <label for="option4">Option 4</label>
    <input
      type="text"
      name="option4"
      id="option4"
      placeholder="Yellow"
      required
    />
    <button type="submit">Create</button>
  </form>
  <dialog id="modal-success">
    <article>
      <h3 style="color: #7cb342;">Success!</h3>
      <p>You poll's ID is: {#if resJ}{resJ.id}{ /if}</p>
      <p>
        Here is the code for your poll. Copy and paste it into the widget field
        on Hashnode:
      </p>
      <p style="color: #ffb300;">Note: Copy this code and save the ID as we have no way of retrieving it once you navigate away from the page!</p>
      <pre><code> &lt;iframe src="https://hashpoll.hackersreboot.tech/vote/{#if resJ}{resJ.id}{ /if}" style="border:0px #ffffff none;" name="myiFrame" scrolling="yes" frameborder="0" marginheight="0px" marginwidth="0px" height="150%" width="100%" allowfullscreen &gt; &lt;/iframe&gt;</code
        ></pre>
      <footer>
        <div class="grid">
          <button class="secondary" on:click={closeDialog}>Cancel</button>
          <button on:click={formRedirect}> Go to form! </button>
        </div>
      </footer>
    </article>
  </dialog>
</main>
