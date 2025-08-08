$$
\frac{
  \Gamma, x : A \vdash e : B
}{
  \Gamma \vdash \lambda x. e : \Pi_{x : A} B
}
$$

I'm a CS undergrad at Yale, primarily interested in programming languages and proof assistants. You can find me on [Github](https://github.com/ehatti) and [LinkedIn](https://www.linkedin.com/in/eashan-hatti-777387288).

{% for post in site.posts %}
  <article>
    <h3>{{ page.title }} -- {{ page.date | date: "%B %-d, %Y" }}</h3>
    {% if post.excerpt %}
      <p>{{ post.excerpt }}</p>
    {% endif %}
    <a href="{{ post.url | relative_url }}">Read more</a>
  </article>
{% endfor %}