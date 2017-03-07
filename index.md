---
title: Clojure/GSoC
layout: cards
---

{% include card.html
  title="What is Clojure/GSoC?"
  content="<blockquote>Google Summer of Code (GSoC) is a program that matches mentoring organizations with college and university student developers who are paid to write open source code.</blockquote>

Clojure will be participating once again as mentoring organisation in 2017.
This means that Google will be paying students from around to world to contribute to projects throughout the Clojure ecosystem.
"
  action1_url="/students/"
  action1_text="Be a student"

  action2_url="/mentors/"
  action2_text="Be a mentor"

  card_classes="mdl-cell--8-col-desktop mdl-cell--5-col"
%}

{% include card.html
  title="What‘s next?"
  content="The student application will open starting on the 20th of March through the 3rd of April."
  action1_url="/assets/ics/student-application-period-2017.ics"
  action1_text="Add to calendar"
  action_icon="event"
  card_classes="mdl-cell--4-col mdl-cell--3-col-tablet"
%}

{% for post in site.posts limit: 4 %}
{% include postcard.html %}
{% endfor %}
