$$
\frac{
  \Gamma, x : A \vdash e : B
}{
  \Gamma \vdash \lambda x. e : \Pi_{x : A} B
}
$$

I am a CS undergrad at Yale, primarily interested in programming languages and proof assistants.

## Links

- [Github](https://github.com/ehatti)
- [LinkedIn](https://www.linkedin.com/in/eashan-hatti-777387288)

## Posts

{% for post in site.posts limit:10 %}
  <article class="post-preview">
    <h2><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h2>
    <p class="post-meta">
      <time datetime="{{ post.date | date_to_xmlschema }}">
        {{ post.date | date: "%B %d, %Y" }}
      </time>
    </p>
    {% if post.excerpt %}
      <p>{{ post.excerpt }}</p>
    {% endif %}
    <a href="{{ post.url | relative_url }}">Read more →</a>
  </article>
{% endfor %}