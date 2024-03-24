---
title: Integrating Disqus Comments in Chirpy Theme for Jekyll
author: Jay Jo
date: 2024-03-02 00:00:00 +09:00
categories: [tip]
tags: [tip]
---

To integrate Disqus comments into your Jekyll site using the Chirpy theme, follow these detailed steps:

### 1. Register Your Site with Disqus

https://disqus.com/

Before you begin, ensure you have a Disqus account and have registered your site. This process will provide you with a unique Disqus shortname, essential for the following steps.

### 2. Configure Disqus in Chirpy

Modify the `_config.yml` file within your Chirpy theme directory to include your Disqus shortname. Update the file as follows:

```yaml
# _config.yml
comments:
  active: "disqus"
  disqus:
    shortname: "your-disqus-shortname"
```

Replace `your-disqus-shortname` with the actual shortname provided by Disqus.

### 3. Enable Comments in Your Posts

To activate comments for a post, add a `comments` variable in the YAML front matter of the post file, setting its value to `true`. Here's an example:

```yaml
---
layout: post
title: "Your Post Title"
comments: true
# other options
---
```

To disable comments, set `comments: false` or omit the `comments` option.

### 4. Update Your Templates

Chirpy should automatically integrate Disqus comments based on your configuration. If necessary, adjust the template files. Typically, the Disqus code is placed in `_layouts/post.html`, within conditional statements:

```
{% raw %}
{% if page.comments %}
  <div id="disqus_thread"></div>
  <script>
  /* Your Disqus embed code */
  </script>
{% endif %}
{% endraw %}
```

Ensure your Chirpy theme is up to date, as template structures may vary between versions.

* How to get Your Disqus embed code

https://help.disqus.com/en/articles/1717112-universal-embed-code

### 5. Test Your Integration

After configuring, test the Disqus integration on your local server or a live site. Verify that the Disqus system appears correctly on a test post with comments enabled.

Follow these steps to successfully add Disqus comments to your Chirpy-themed Jekyll blog. Consult the Chirpy theme documentation or Disqus integration guide for further assistance.