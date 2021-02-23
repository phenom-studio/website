<section id="contact">

  <form name="contact" method="POST" class="form">

    <div>
      <input type="hidden" name="form-name" value="contact" />
      <label for="email">Email address</label>
      <input
        type="email"
        name="email"
        aria-describedby="emailHelp"
        placeholder="Enter email" />
    </div>

    <div>
      <label for="subject">Subject</label>
      <input type="text" name="subject" placeholder="Enter subject" />
    </div>

    <div>
      <label for="message">Message</label>
      <textarea name="message" rows="3" placeholder="Enter your message here" />
    </div>

    <button type="submit" id="submit">Submit</button>

  </form>

</section>

<style>
    .form {
      display: flex;
      flex-direction: column;
      justify-content: space-around;
    }
  
    input,
    textarea {
      width: 100%;
    }
  
    #submit {
      background-color: #1e2122;
      transition: all 0.3s ease 0s;
    }
  
    #submit:hover {
      background-color: white;
    }
  </style>