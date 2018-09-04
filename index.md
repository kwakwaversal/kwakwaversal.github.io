## Programming and devops musings

The hope is that I will be articulating the things I discover when following
the black hole after I get a thought in my head.

### Posts

<dl class="posts">
  {% for post in site.posts %}
    <dt>
		<a class="post-link" href="{{ post.url | relative_url }}">{{ post.title }}</a> {{ post.date | date: "%b %-d, %Y" }}
    </dt>
<br/>
  {% endfor %}
</dl>
