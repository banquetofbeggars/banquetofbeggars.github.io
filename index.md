Hello and welcome to my website.
This is the top-level page in the website.
There are some interesting files [here](_posts/test.md), and [here](_posts/test_two.md)
There is an experimental link to more posts in a subfolder [here](_posts/another_md.md)

ThreeJS app examples can be found [here](_posts/threejs-example.md).

Alterations to the page layout can be made by changing default.html, and the styles in style.css

Most markdown tags are turned into standard html elements.
The configuration of these can be changed by overwriting it style.css.

<ul>
    {% for post in site.posts %}
        <li>
            <a href="{{ site.post }}">{{post.title}}</a>
        </li>
    {% endfor %}
</ul>