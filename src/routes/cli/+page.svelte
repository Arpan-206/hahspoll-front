<script>
</script>

<svelte:head>
  <title>Hashpoll CLI</title>
  <meta name="description" content="Hash Poll" />
</svelte:head>

<main>
  <h1>Hashpoll CLI</h1>

  <p style="text-align: justify-content; text-justify: inter-word;">
    Hashpoll CLI is a handy tool to extend and supplement Hashpoll. It allows
    you to seamlessly create polls from the command line. The tool automatically
    gives you the code to place in the widgets section of Hashnode.
  </p>
  <div class="grid">
    <div>
    <a
      href="https://github.com/Arpan-206/hashpoll-cli"
      role="button"
      class="contrast outline"
      >Check out the Repo!</a
    ></div>
    <div>
        <a href="https://pypi.org/project/hashpoll-cli/" role="button" class="outline">Check out on PyPi!</a>
    </div>
  </div>

  <div style="padding-top: 2rem;" class="container-fluid">
    <div class="container">
      <h2>Installation</h2>
      <p>
        To install Hashpoll CLI, run the following command in your terminal:
      </p>
      <pre><code>pip install hashpoll-cli</code></pre>
      <p>
        This will install the tool globally on your system. You can then run the
        tool by typing <code>hashpoll</code> in your terminal. If it doesn't
        work, then try running <code>python -m hashpoll</code>.
      </p>
    </div>
    <div class="container">
      <h2>Commands</h2>
      <p>Hashpoll CLI has many commands for you to use. Some of them are:</p>
      <div>
        <h3>Create</h3>
        <p>This is the command to create polls from the CLI.</p>
        <pre><code
            >hashpoll create [question] --option1 [option1] --option2 [option2] --option3 [option3] --option4 [option4]</code
          ></pre>
        <script
          id="asciicast-pZfU2ZIyot72RmtSD6yzfSioz"
          src="https://asciinema.org/a/pZfU2ZIyot72RmtSD6yzfSioz.js"
          asyncr></script>
        <div>
          <h4>Tips</h4>
          <ul>
            <li>
              Put the question or options (if multiple words) in quotes to avoid
              the terminal registering this as multiple arguments.
            </li>
            <li>
              If you miss adding one of the options, the program will prompt you
              for entering them.
            </li>
          </ul>
        </div>
      </div>
      <div>
        <h3>View</h3>
        <p>This is a command for viewing all details of a particular poll.</p>
        <pre><code>hashpoll view [Poll ID]</code></pre>
        <script
          id="asciicast-LHrMNStGjVkRMP4hbGu5otF0L"
          src="https://asciinema.org/a/LHrMNStGjVkRMP4hbGu5otF0L.js"
          async></script>
      </div>
      <div>
        <h3>Vote</h3>
        <p>This is a command to vote on a specific poll.</p>
        <pre><code>hashpoll vote [Poll ID] [Option Number]</code></pre>
        <script
          id="asciicast-1FDpi9gaVHZqeaLuxKAnjXecg"
          src="https://asciinema.org/a/1FDpi9gaVHZqeaLuxKAnjXecg.js"
          async></script>
      </div>
      <div>
        <h3>Open-poll</h3>
        <p>This is a simple command to open a poll in the default browser.</p>
        <pre><code>hashpoll open-poll [Poll ID]</code></pre>
        <script
          id="asciicast-wA9D9Smrwx3H1dVkiaXZ1FzWC"
          src="https://asciinema.org/a/wA9D9Smrwx3H1dVkiaXZ1FzWC.js"
          async></script>
      </div>
      <div>
        <h3>Results</h3>
        <p>This is a command to fetch the current data from poll responses.</p>
        <pre><code>hashpoll results [Poll ID]</code></pre>
        <script
          id="asciicast-p455OvYTuy6e7Q9bECDWWDkbT"
          src="https://asciinema.org/a/p455OvYTuy6e7Q9bECDWWDkbT.js"
          async></script>
      </div>
      <div>
        <h3>Code</h3>
        <p>
          This is handy commad to generate the Hashnode Widget Code for a
          particular poll.
        </p>
        <pre><code>hashpoll code [Poll ID]</code></pre>
        <script
          id="asciicast-0R0xeOpRnSphSxKHOvVNcq2uR"
          src="https://asciinema.org/a/0R0xeOpRnSphSxKHOvVNcq2uR.js"
          async></script>
      </div>
    </div>
  </div>
</main>
