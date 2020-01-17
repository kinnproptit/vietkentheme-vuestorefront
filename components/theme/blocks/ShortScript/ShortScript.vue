<template>
  <section class="short-script">
    <div class="content-card image left-image no-margin-btm">
      <div
        class="media"
        style="background-image: url('https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/pages/content-mortar-pestle-chamomile-oregano.jpg');background-position: center 45%;padding-top:40%;"
      >
        <img
          class="u-hiddenVisually"
          src="https://cdn8.bigcommerce.com/s-zsd73psd0i/content/assets/seo/images/pages/content-mortar-pestle-chamomile-oregano.jpg"
          alt="Image of mortar and pestle with Chamomile and Oregano."
        />
      </div>
      <div class="content">
        <div class="content-header">
          <h3>The New Chapter tradition.</h3>
        </div>
        <div class="content-body">
          <p>
            New Chapter
            <sup>®</sup> was founded over 35 years ago to bring natural wellness to others. We believe in the healing power of nature, and that's why we're committed to using whole-food and quality ingredients to make our supplements.
          </p>
        </div>
        <div class="content-footer">
          <a
            class="button button--primary"
            href="https://www.newchapter.com/tradition/"
          >Explore our story</a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'ShortScript'
}
</script>

<style lang="scss" scoped>
.short-script {
  @media (min-width: 801px) {
    .content-card.image {
      margin: 6rem 0 3rem;
    }
  }

  @media (min-width: 1180px) {
    .content-card.image {
      margin-top: 3rem;
    }
  }

  .no-margin-btm {
    margin-bottom: 0 !important;
  }

  @media (min-width: 1180px) {
    .content-card {
      flex-direction: row !important;
      padding: 4.0625rem 3.75rem;
    }
  }

  .content-card {
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    margin: 7rem 0;
    padding: 3rem 1.5rem;
    background: #f9f8f3;
    flex-direction: column;
  }

  @media (min-width: 551px) {
    .media {
      padding-top: 40%;
    }
  }

  @media (min-width: 1180px) {
    .content-card .media {
      display: flex;
      padding-left: 0.75rem;
      padding-right: 0.75rem;
      margin-bottom: 0;
      width: 40%;
    }
    .content-card.left-image .content {
      padding-left: 4.5rem;
    }
  }
  .content-card .media {
    margin-bottom: 3rem;
    padding-top: 84%;
    width: 100%;
    margin-top: -7.5rem;
    position: relative;
    background-repeat: no-repeat;
    background-size: cover;
    max-width: 100%;
    float: none;
  }
  .content-card .media {
    height: auto;
    box-shadow: 0 30px 70px -20px rgba(0, 0, 0, 0.5),
      0 53px 50px -50px rgba(0, 0, 0, 0.5);
  }

  .u-hiddenVisually {
    border: 0 !important;
    clip: rect(1px, 1px, 1px, 1px) !important;
    height: 1px !important;
    overflow: hidden !important;
    padding: 0 !important;
    position: absolute !important;
    width: 1px !important;
  }

  .content-card .content .content-header h3 {
    margin: 0 0 0.5rem;
    font-size: 1.625rem;
    line-height: initial;
    letter-spacing: -1px;
  }

  @media (min-width: 551px) {
    .content-card .content .content-header h3 {
      font-size: 2.625rem;
    }
  }

  @media (min-width: 801px) {
    .content-card .content .content-header h3 {
      font-size: 3.3125rem;
    }
  }

  .content-body {
    color: #4a4a4a;
  }

  .button {
    border-style: solid;
    border-width: 1px;
    cursor: pointer;
    font-weight: 400;
    margin: 0 0 1rem;
    position: relative;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    background-color: transparent;
    border-color: #ccc;
    color: #666;
    font-size: 1rem;
    padding: 0.875rem 2.25rem;
    border-radius: 4px;
    outline: 0;
    vertical-align: middle;
  }

  .button--primary {
    background-color: #795548;
    border-color: #795548;
    color: #fefefe;
  }
}
</style>
