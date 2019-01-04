---
title: Javascript URLs
categories:
- InfoSec
# feature_image: "https://picsum.photos/2560/600?image=872"
---

If someone says link, the typical thing you think of would be a http or https url. However, even something as simple as allowing users to submit an url can be a security issue.

A few weeks ago, I found a vulnerability in the configuration of a website's markdown library. This allowed users to submit insecure links, such as
```markdown
[Test Link](javascript:alert('Pwned'))
```
which translates to
```html
<a href="javascript:alert('Pwned')">Test Link</a>
```
If saved in a database (like in this case), it is a persistent XSS vulnerability, executing when you click it. The issue on the website was fixed within one hour.

It's well known that trusting user input is dangerous, and this is an example of yet another avenue it can be abused. An avenue a lot of application developers might not even know about.

To secure against this, you should only allow http or https as protocols for user submitted links. And you can also look at some more recommendations, such as [The 2018 Guide to Building Secure PHP Software](https://paragonie.com/blog/2017/12/2018-guide-building-secure-php-software), written by Paragon Initiative, which also contain a lot of general tips that apply to all programming languages.
