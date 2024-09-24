---
title: Contact
nav:
  order: 5
  tooltip: Email, address, and location
---

# {% include icon.html icon="fa-regular fa-envelope" %}Contact

Department of Electrical and Computer Engineering, The University of Alabama in Huntsville
Huntsville, AL 3589

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

{% capture col2 %}

{%
  include figure.html
  image="images/photo.jpg"
  caption="Lorem ipsum"
%}

{% endcapture %}

{% include cols.html col1=col1 col2=col2 %}

{% include section.html dark=true %}

{% capture col1 %}
Lorem ipsum dolor sit amet  
consectetur adipiscing elit  
sed do eiusmod tempor
{% endcapture %}

{% capture col2 %}
Lorem ipsum dolor sit amet  
consectetur adipiscing elit  
sed do eiusmod tempor
{% endcapture %}

{% capture col3 %}
Lorem ipsum dolor sit amet  
consectetur adipiscing elit  
sed do eiusmod tempor
{% endcapture %}

{% include cols.html col1=col1 col2=col2 col3=col3 %}
