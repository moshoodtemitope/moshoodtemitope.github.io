<!DOCTYPE html>
<html lang="{{ site.lang | default: "en-US" }}">
{% include siteheader.html %}
  <body>
    
    <section class="main-page-header">
      <div class="site-header">
        <div class="my-fav">
          <a href="/"> <img alt="" src="/assets/images/header-fav.png"></a>
        </div>
        
        <nav class="main-nav">
          <a href="/">Home</a>
          <a href="/about/">About me</a>
          <a href="/category/lets-build-series.html" class="lets-build">Let's Build Series</a>
          <!-- <a href="/writing/" class="blog-link">Blog</a> -->
        </nav>
      </div>
      
      <div class="post-header">
        <div class="title-of-post">
          <h1>{{ page.title }}</h1>
          <span class="list-post-tags">
          {% if page.tags.size > 0 %}<i class="fa fa-tags" aria-hidden="true"></i>{% endif %}
          
            {% for tag in page.tags %}
              {% capture tag_name %}{{ tag }}{% endcapture %}
              {% if forloop.last == false %}
                <!--<a href="/tag/{{ tag_name }}">{{ tag_name }}</a>,-->
                <a href="#">{{ tag_name }}</a>,
                {% else %}
                <!--<a href="/tag/{{ tag_name }}">{{ tag_name }}</a>-->
                <a href="#">{{ tag_name }}</a>
              {% endif %}
            {% endfor %}
          
        </span>
        </div>
        <div class="post-meta">
          <div class="author-photo">
              <img alt="" src="/assets/images/mrmosh.jpg">
          </div>
          <div class="author-and-date">
              <h3><a href="/about"> Moshood Temitope</a></h3>
              <span class="meta">{{ page.date | date_to_string }}</span> 
              <span class="middle-dot">&middot;</span>
              <span class="time-to-read">
                  {% assign words = content | number_of_words %}
                  {% if words < 270 %}
                    1 min
                  {% else %}
                    {{ words | divided_by:135 }} mins
                {% endif %} read
              </span>
          </div>
          
        </div>
        
      </div>
    </section>
    
    <section class="post-content-wrap">
      <div class="post">
        {{ content }}
      </div>

      
      <div class="say-hello-wrap">
        <div class="comments-allowed">
          Enjoy this post? Kindly share with the community <img src="data:image/svg+xml;utf8;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iaXNvLTg4NTktMSI/Pgo8IS0tIEdlbmVyYXRvcjogQWRvYmUgSWxsdXN0cmF0b3IgMTkuMC4wLCBTVkcgRXhwb3J0IFBsdWctSW4gLiBTVkcgVmVyc2lvbjogNi4wMCBCdWlsZCAwKSAgLS0+CjxzdmcgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIiB4bWxuczp4bGluaz0iaHR0cDovL3d3dy53My5vcmcvMTk5OS94bGluayIgdmVyc2lvbj0iMS4xIiBpZD0iTGF5ZXJfMSIgeD0iMHB4IiB5PSIwcHgiIHZpZXdCb3g9IjAgMCA1MTIuMDAxIDUxMi4wMDEiIHN0eWxlPSJlbmFibGUtYmFja2dyb3VuZDpuZXcgMCAwIDUxMi4wMDEgNTEyLjAwMTsiIHhtbDpzcGFjZT0icHJlc2VydmUiIHdpZHRoPSI1MTJweCIgaGVpZ2h0PSI1MTJweCI+CjxjaXJjbGUgc3R5bGU9ImZpbGw6I0Y3QjIzOTsiIGN4PSIyNTYuMDA0IiBjeT0iMjU2LjAwNCIgcj0iMjQ2Ljg1NSIvPgo8Zz4KCTxwYXRoIHN0eWxlPSJmaWxsOiNFMDlCMkQ7IiBkPSJNMTI2LjMwNiwzODUuNjk0Yy04OC44MDEtODguODAyLTk1Ljc5OC0yMjguNDI2LTIwLjk5OC0zMjUuMjQyICAgQzk3LjAyMyw2Ni44NTMsODkuMDUxLDczLjg1LDgxLjQ1LDgxLjQ1Yy05Ni40MDEsOTYuNDAxLTk2LjQwMSwyNTIuNjk4LDAsMzQ5LjA5OXMyNTIuNjk4LDk2LjQwMSwzNDkuMDk5LDAgICBjNy41OTktNy41OTksMTQuNTk3LTE1LjU3MywyMC45OTktMjMuODU4QzM1NC43MzMsNDgxLjQ5MiwyMTUuMTA4LDQ3NC40OTQsMTI2LjMwNiwzODUuNjk0eiIvPgoJPHBhdGggc3R5bGU9ImZpbGw6I0UwOUIyRDsiIGQ9Ik0yNTYuMDAxLDQwMC44MzFjLTE0Ljc1NiwwLTI5LjUwNS0yLjAxLTQzLjg1LTYuMDMxYy00Ljg2NS0xLjM2NC03LjcwNC02LjQxNC02LjM0LTExLjI4MSAgIGMxLjM2NC00Ljg2NSw2LjQxNC03LjcwNiwxMS4yOC02LjM0YzI1LjQ1NSw3LjEzNyw1Mi4zNjYsNy4xMzcsNzcuODIxLDBjNC44NjktMS4zNjEsOS45MTYsMS40NzUsMTEuMjgsNi4zNCAgIHMtMS40NzUsOS45MTYtNi4zNCwxMS4yOEMyODUuNTA5LDM5OC44MiwyNzAuNzUxLDQwMC44MzEsMjU2LjAwMSw0MDAuODMxeiIvPgo8L2c+CjxwYXRoIGQ9Ik0yNTYuMDAxLDBDMTE0Ljg0MSwwLDAsMTE0Ljg0MSwwLDI1Ni4wMDFzMTE0Ljg0MSwyNTYuMDAxLDI1Ni4wMDEsMjU2LjAwMVM1MTIuMDAxLDM5Ny4xNiw1MTIuMDAxLDI1Ni4wMDEgIEM1MTIsMTE0Ljg0MSwzOTcuMTYsMCwyNTYuMDAxLDB6IE0yNTYuMDAxLDQ5My43MDFjLTEzMS4wNjksMC0yMzcuNzAyLTEwNi42MzEtMjM3LjcwMi0yMzcuN1MxMjQuOTMyLDE4LjI5OSwyNTYuMDAxLDE4LjI5OSAgczIzNy43MDIsMTA2LjYzMiwyMzcuNzAyLDIzNy43QzQ5My43MDEsMzg3LjA3LDM4Ny4wNjgsNDkzLjcwMSwyNTYuMDAxLDQ5My43MDF6Ii8+CjxwYXRoIGQ9Ik0zODAuMTAxLDI5NS43MjNjLTY4LjQzMiw2OC40My0xNzkuNzc4LDY4LjQyOC0yNDguMjAzLDBjLTMuNTc0LTMuNTczLTkuMzY3LTMuNTczLTEyLjk0LDAgIGMtMy41NzMsMy41NzMtMy41NzMsOS4zNjcsMCwxMi45MzljMzcuNzg4LDM3Ljc4Niw4Ny40MDUsNTYuNjczLDEzNy4wNDIsNTYuNjczYzQ5LjYyMywwLDk5LjI2My0xOC44OTYsMTM3LjA0Mi01Ni42NzMgIGMzLjU3My0zLjU3MywzLjU3My05LjM2NywwLTEyLjkzOUMzODkuNDY4LDI5Mi4xNSwzODMuNjc2LDI5Mi4xNDksMzgwLjEwMSwyOTUuNzIzeiIvPgo8cGF0aCBkPSJNMTQ2LjcyMywyMzEuOTc0YzE4LjY2NiwwLDMzLjg1Mi0xNS4xODYsMzMuODUyLTMzLjg1MnMtMTUuMTg2LTMzLjg1Mi0zMy44NTItMzMuODUycy0zMy44NTIsMTUuMTg2LTMzLjg1MiwzMy44NTIgIFMxMjguMDU4LDIzMS45NzQsMTQ2LjcyMywyMzEuOTc0eiIvPgo8cGF0aCBkPSJNMzY1LjI3NSwxNjQuMjdjLTE4LjY2NiwwLTMzLjg1MiwxNS4xODYtMzMuODUyLDMzLjg1MnMxNS4xODYsMzMuODUyLDMzLjg1MiwzMy44NTJzMzMuODUyLTE1LjE4NiwzMy44NTItMzMuODUyICBTMzgzLjk0MiwxNjQuMjcsMzY1LjI3NSwxNjQuMjd6Ii8+CjxnPgoJPGNpcmNsZSBzdHlsZT0iZmlsbDojRkZGRkZGOyIgY3g9IjE1NS45NjkiIGN5PSIxOTMuNTA3IiByPSI5LjE1Ii8+Cgk8Y2lyY2xlIHN0eWxlPSJmaWxsOiNGRkZGRkY7IiBjeD0iMzc0LjMzOCIgY3k9IjE5My41MDciIHI9IjkuMTUiLz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8Zz4KPC9nPgo8L3N2Zz4K" />
        </div>
        <div class="social-share">
            <span>Share &rarr;</span> 
          
          <!--[if lt IE 9]
          <a class="twitter-share-button"  href="https://twitter.com/intent/tweet?text={{ page.title }} by 
          @{{ site.twitter.username }} -&url={{ site.url }}{{ page.url }}" rel="nofollow" target="_blank" title="Share on Twitter">
            <i class="fa fa-twitter" aria-hidden="true"></i>
          </a>
          <a href="https://facebook.com/sharer.php?u={{ site.url }}{{ page.url }}" class="fb-button" rel="nofollow" target="_blank" title="Share on Facebook">
            <i class="fa fa-facebook-f" aria-hidden="true"></i>
          </a>
          <![endif]-->
          <a href="https://twitter.com/intent/tweet?text={{ page.title }} by @{{ site.twitter.username }} -&url={{ site.url }}{{ page.url }}" rel="nofollow" target="_blank" title="Share on Twitter" class="twitter-share-button svg-icon">
            <svg viewBox="0 0 512 512">
              <path fill="#ffffff" d="M419.6 168.6c-11.7 5.2-24.2 8.7-37.4 10.2 13.4-8.1 23.8-20.8 28.6-36 -12.6 7.5-26.5 12.9-41.3 15.8 -11.9-12.6-28.8-20.6-47.5-20.6 -42 0-72.9 39.2-63.4 79.9 -54.1-2.7-102.1-28.6-134.2-68 -17 29.2-8.8 67.5 20.1 86.9 -10.7-0.3-20.7-3.3-29.5-8.1 -0.7 30.2 20.9 58.4 52.2 64.6 -9.2 2.5-19.2 3.1-29.4 1.1 8.3 25.9 32.3 44.7 60.8 45.2 -27.4 21.4-61.8 31-96.4 27 28.8 18.5 63 29.2 99.8 29.2 120.8 0 189.1-102.1 185-193.6C399.9 193.1 410.9 181.7 419.6 168.6z"/>
            </svg>
          </a>
          
          
          <a href="https://facebook.com/sharer.php?u={{ site.url }}{{ page.url }}" class="fb-button svg-icon" rel="nofollow" target="_blank" title="Share on Facebook">
            <svg viewBox="0 0 512 512">
              <path fill="#FFFFFF" d="M211.9 197.4h-36.7v59.9h36.7V433.1h70.5V256.5h49.2l5.2-59.1h-54.4c0 0 0-22.1 0-33.7 0-13.9 2.8-19.5 16.3-19.5 10.9 0 38.2 0 38.2 0V82.9c0 0-40.2 0-48.8 0 -52.5 0-76.1 23.1-76.1 67.3C211.9 188.8 211.9 197.4 211.9 197.4z"/>
            </svg>
          </a>
        </div>
      </div>
      <div class="navigate-between-pages">
        {% if page.previous.url %}
          <div class="pre-wrap">
            <span>Previous post</span> 
            <a class="prev" href="{{page.previous.url}}">&laquo; {{page.previous.title}}</a>
          </div>
        {% endif %}
        {% if page.next.url %}
          <div class="pre-wrap">
            <span>Next post</span> 
            <a class="next" href="{{page.next.url}}">{{page.next.title}} &raquo;</a>
          </div>
          
        {% endif %}
      </div>
      
      {% include subscribe.html %}
      <footer class="">
        <div class="post-footer">
          <div class="author-photo">
              <img alt="" src="/assets/images/mrmosh.jpg">
          </div>
        
          <div class="author-meta-info">
            <h3 class="name-of-author"><a href="/about">Moshood Temitope</a></h3>
            <div class="who-is-author">
              <span class="author-job-roles">FE Engineer</span>
              <span class="job-separator">&middot;</span>
              <span class="author-job-roles">UI Designer</span>
              <span class="job-separator">&middot;</span>  
              <span class="author-job-roles">UX Researcher</span>
            </div>
          </div>
        </div>
        <div class="site-footer">
          &copy; 2018. All rights reserved
          <a href="/contact"> Contact me</a>
        </div>
      </footer>
      {% if page.comments %} 
        <div id="disqus_thread"></div>
        <script>

        /**
        *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
        *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
        /*
        var disqus_config = function () {
        this.page.url = {{ site.url }}{{ page.url }};  // Replace PAGE_URL with your page's canonical URL variable
        this.page.identifier = {{ page.url }}; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
        };
        */
        (function() { // DON'T EDIT BELOW THIS LINE
        var d = document, s = d.createElement('script');
        s.src = 'https://https-moshoodtemitope-com.disqus.com/embed.js';
        s.setAttribute('data-timestamp', +new Date());
        (d.head || d.body).appendChild(s);
        })();
        </script>
        <noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
                            
    {% endif %}
    </section>
    {%if page.isJsPost == true %}
     
    {% endif %}

    
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

