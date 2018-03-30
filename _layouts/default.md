<!DOCTYPE html>
<html lang="{{ site.lang | default: "en-US" }}">
  {% include siteheader.html %}
  <body>
    <section class="main-page-header ">
      <div class="site-header">
        <div class="my-fav">
          <a href="/"> <img alt="" src="/assets/images/header-fav.png"></a>
        </div>
        
        <nav class="main-nav" id="main-nav">
          <a href="/about/">About me</a>
          <a href="/category/lets-build-series.html" class="lets-build">Let's Build Series</a>
          <!-- <a href="/writing/" class="blog-link">Blog</a> -->
        </nav>
      </div>
      
      
      
      
    </section>

    <section class="main-content">
      {{ content }}

      {% include subscribe.html %}
      
    </section>
    <footer class="site-footer">
      <div class="footer-content">
        &copy; 2018. All rights reserved
        <a href="/contact"> Contact me</a>
      </div>
    </footer>
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

    <!-- Global site tag (gtag.js) - Google Analytics -->
    <script async src="https://www.googletagmanager.com/gtag/js?id=UA-116683659-1"></script>
    <script>
      window.dataLayer = window.dataLayer || [];
      function gtag(){dataLayer.push(arguments);}
      gtag('js', new Date());

      gtag('config', 'UA-116683659-1');
    </script>


  </body>
</html>
