---
title: Contact
nav:
  order: 5
  tooltip: Email, address, and location
---

# {% include icon.html icon="fa-regular fa-envelope" %}Contact



<div style="text-align: center;">
Department of Electrical and Computer Engineering, <br/>The University of Alabama in Huntsville
Huntsville, AL 35899
</div>

{%
  include button.html
  type="email"
  text="rahul.bhadani@uah.edu"
  link="rahul.bhadani@uah.edu"
%}
{%
  include button.html
  type="phone"
  text="256-824-6302"
  link="+1-256-824-6302"
%}
{%
  include button.html
  type="address"
  tooltip="UAH ECE"
  link="https://ece.uah.edu/"
%}

{% include section.html %}

{% capture col1 %}

{%
  include figure.html
  image="images/photo10.JPG"
  caption="PI"
%}

{% endcapture %}

{% include cols.html col1=col1%}

{% include section.html dark=true %}

{% capture col1 %}
The University of Alabama in Huntsville
301 Sparkman Drive
Huntsville, AL 35899
{% endcapture %}

{% capture col2 %}
256.824.1000
{% endcapture %}

{% capture col3 %}
<a href="https://www.uah.edu/contact">https://www.uah.edu/contact</a>
{% endcapture %}

{% include cols.html col1=col1 col2=col2 col3=col3 %}
