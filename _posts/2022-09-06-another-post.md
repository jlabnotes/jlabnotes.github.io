---
title: Antoher Post Simple
date: 2022-09-06
categories: [HOMELAB,SOFTWARE]
tags: [desktop,dell,simple]

---

## Another post here  
This is another post  

## Customizing Stylesheet
If you need to customize the stylesheet, copy the theme's assets/css/style.scss{: .filepath} to the same path on your Jekyll site, and then add the custom style at the end of the style file.

Starting from v4.1.0, if you want to overwrite the SASS variables defined in _sass/addon/variables.scss{: .filepath}, create a new file _sass/variables-hook.scss{: .filepath} and assign new values to the target variable in it.

## Here expand and collapse example
<details>
<summary><strong>Click for more details</strong></summary>
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis eget congue risus. Nulla in purus velit. Pellentesque non dolor aliquet, feugiat ligula vitae, lobortis nibh. Fusce placerat dolor ipsum, sit amet viverra felis laoreet ut. Proin ultrices sem placerat congue porta. Maecenas ut sapien mollis mauris posuere semper.
</details>

Whenever you need to post a code snippet, use the liquid tags `hilight` and `endhilight` like this:

{% highlight ruby %}
# some code goes here
puts "Hello World!"
{% endhighlight %}

To add an icon somewhere in the template simply do:

{% highlight html %}
<i class="icon-info"></i>
{% endhighlight %}
