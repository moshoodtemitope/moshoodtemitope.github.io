<!DOCTYPE html>
<html lang="{{ site.lang | default: "en-US" }}">
  {% include siteheader.html %}
  <body>
    <section class="main-page-header">
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
      <div class="main-header text-center">
        <div class="single-page-heading">
          <h1>{{page.title}}</h1>
          <div class="page description"><h3>{{page.pageDesc}}</h3></div>
        </div>
      </div>
    </section>

    <section class="main-content">
      {{ content }}

     {% include sitefooter.html %}
