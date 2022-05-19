<script>
  import { url } from "../Utils/service";

  let name, email, subject, message;

  async function sendForm(e) {
    e.preventDefault();

    const mess = {
      name: name.value,
      email: email.value,
      subject: subject.value,
      message: message.value,
    };
    async function postData(url = "", data = {}) {
      const response = await fetch(url, {
        method: "POST",
        mode: "cors",
        cache: "no-cache",
        credentials: "same-origin",
        headers: {
          "Content-Type": "application/json",
        },
        redirect: "follow",
        referrerPolicy: "no-referrer",
        body: JSON.stringify(mess),
      });
      return response.json();
    }

    postData(url, { answer: 42 }).then((data) => {
      console.log(data);
    });
  }
</script>

<main>
  <section id="contact" class="contact">
    <div class="container" data-aos="fade-up">
      <div class="section-title">
        <h2>Contact</h2>
      </div>

      <div class="row mt-1">
        <div class="col-lg-4">
          <div class="info">
            <div class="address">
              <i class="bi bi-geo-alt" />
              <h4>Location:</h4>
              <p>A108 Pamukkale, Denizli, NY 535022</p>
            </div>

            <div class="email">
              <i class="bi bi-envelope" />
              <h4>Email:</h4>
              <p>info@example.com</p>
            </div>

            <div class="phone">
              <i class="bi bi-phone" />
              <h4>Call:</h4>
              <p>+1 5589 55488 55s</p>
            </div>
          </div>
        </div>

        <div class="col-lg-8 mt-5 mt-lg-0">
          <form on:submit={sendForm} method="post" class="php-email-form">
            <div class="row">
              <div class="col-md-6 form-group">
                <input
                  type="text"
                  name="name"
                  class="form-control"
                  id="name"
                  placeholder="Your Name"
                  required
                  bind:this={name}
                />
              </div>
              <div class="col-md-6 form-group mt-3 mt-md-0">
                <input
                  type="email"
                  class="form-control"
                  name="email"
                  id="email"
                  placeholder="Your Email"
                  required
                  bind:this={email}
                />
              </div>
            </div>
            <div class="form-group mt-3">
              <input
                type="text"
                class="form-control"
                name="subject"
                id="subject"
                placeholder="Subject"
                required
                bind:this={subject}
              />
            </div>
            <div class="form-group mt-3">
              <textarea
                class="form-control"
                name="message"
                rows="5"
                placeholder="Message"
                required
                bind:this={message}
              />
            </div>
            <div class="my-3">
              <div class="loading">Loading</div>
              <div class="error-message" />
              <div class="sent-message">
                Your message has been sent. Thank you!
              </div>
            </div>
            <div class="text-center">
              <button type="submit">Send Message</button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </section>
</main>

<style>
</style>
