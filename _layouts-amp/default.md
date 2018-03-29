<!DOCTYPE html>
<html lang="{{ site.lang | default: "en-US" }}">
  {% include siteheader.html %}
  <body>
    <section class="main-page-header">
      <nav class="main-nav">
        <a href="/about/">About me</a>
        <a href="/category/lets-build-series.html" class="lets-build">Let's Build Series</a>
        <!-- <a href="/writing/" class="blog-link">Blog</a> -->
      </nav>
      <div class="main-header text-center">
        <div class="my-photo">
          <img alt="" src="/assets/images/mrmosh.jpg">
        </div>
        <div class="name-of-site">
          <h1>Moshood Temitope</h1>
        </div>
        <div class="who-am-i">
          <span>FrontEnd Engineer</span>
          <span>User Interface Designer</span>  
          <span>User Experience Researcher</span>
        </div>
        <!-- <div class="connect-with-me">
          <a href="https://twitter.com/moreshud15?ref_src=twsrc%5Etfw" class="twitter-follow-button" data-show-count="false">Follow @moreshud15</a>
          
          
          <a class="github-button" href="https://github.com/moshoodtemitope" aria-label="Follow @moshoodtemitope on GitHub">Follow @moshoodtemitope</a>
        </div> -->

      </div>
    </section>

    <section class="main-content">
      {{ content }}

      <footer class="site-footer">
       &copy; 2017. All rights reserved
      </footer>
    </section>
    <!-- Place this tag in your head or just before your close body tag. -->
    <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
    <script async defer src="https://buttons.github.io/buttons.js"></script>
    {% if site.google_analytics %}
      <script type="text/javascript">
        (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
        (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
        m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
        })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

        ga('create', '{{ site.google_analytics }}', 'auto');
        ga('send', 'pageview');
      </script>
    {% endif %}

  </body>
</html>
