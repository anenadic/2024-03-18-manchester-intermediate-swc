---
layout: workshop      # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
venue: "University of Manchester"        # brief name of the institution that hosts the workshop without address (e.g., "Euphoric State University")
address: "Collab 1 & 2, Kilburn Building, Oxford Rd, Manchester M13 9PL"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria"), videoconferencing URL, or 'online'
country: "gb"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) for the institution that hosts the workshop
language: "en"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) for the workshop
latitude: "53.46755727789872"        # decimal latitude of workshop venue (use https://www.latlong.net/)
longitude: "-2.234002998130301"       # decimal longitude of the workshop venue (use https://www.latlong.net)
humandate: "18 - 22 March 2024"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "9:30 - 16:30 BST (UTC + 1)"    # human-readable times for the workshop e.g., "9:00 am - 4:30 pm CEST (7:00 am - 2:30 pm UTC)"
startdate: 2024-03-18      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2024-03-22        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Doug Lowe", "Ann Gledson"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["Anja Le Blanc", "Aman Goel", "Aleksandra Nenadic", "Emma Simpson", "Scott Archer-Nicholls"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["anja.leblanc@manchester.ac.uk"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes:  # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document (e.g., https://pad.carpentries.org/2015-01-01-euphoria)
eventbrite:           # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

<h2 id="general">General Information</h2>

This course aims to teach a core set of established, intermediate-level software development skills and best practices for working as part of a team in a research environment using Python as an example programming language. It focusses on researchers from the [Natural Environment Research Council (NERC)](https://www.ukri.org/councils/nerc/) domain as it uses the dataset from the river catchment study project but is general enough to be attended by participants without this specialism.

{% comment %}
AUDIENCE

Explain who your audience is.  (In particular, tell readers if the
workshop is only open to people from a particular institution.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/who.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/who.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/who.html %}
{% endif %}

{% assign begin_address = page.address | slice: 0, 4 | downcase  %}
{% if page.address == "online" %}
{% assign online = "true_private" %}
{% elsif begin_address contains "http" %}
{% assign online = "true_public" %}
{% else %}
{% assign online = "false" %}
{% endif %}
{% if page.latitude and page.longitude and online == "false" %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}} (get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latitude}}&mlon={{page.longitude}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latitude}},{{page.longitude}}">Google Maps</a>). Participants joining online will receive
  separate joining instructions via email.
</p>
{% elsif online == "true_public" %}
<p id="where">
  <strong>Where:</strong>
  online at <a href="{{page.address}}">{{page.address}}</a>.
  If you need a password or other information to access the training,
  the instructor will pass it on to you before the workshop.
</p>
{% elsif online == "true_private" %}
<p id="where">
  <strong>Where:</strong> This training will take place online.
  The instructors will provide you with the information you will need to connect to this meeting.
</p>
{% endif %}

{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

<p id="requirements">
  <strong>Requirements:</strong>
  {% if online == "false" %}
    Participants must bring a laptop with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% else %}
    Participants must have access to a computer with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% endif %}
  They should have a few specific software packages installed (listed at the <a href="https://carpentries-incubator.github.io/python-intermediate-development-earth-sciences/setup.html">setup page</a>).
</p>

<p id="accessibility">
  <strong>Accessibility:</strong>
  We are committed to making this workshop
  accessible to everybody. The teaching room is wheelchair accessible and accessible restrooms are available.
</p>

<p id="coc">
  <strong>Code of Conduct:</strong>
Everyone who participates in the workshop is required to conform to the <a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">Code of Conduct</a>. Please get in touch with the workshop contact in case of any incidents.
</p>

<p id="contact">
  <strong>Contact:</strong>
  Please email
  {% if page.email %}
  {% for email in page.email %}
  {% if forloop.last and page.email.size > 1 %}
  or
  {% else %}
  {% unless forloop.first %}
  ,
  {% endunless %}
  {% endif %}
  <a href='mailto:{{email}}'>{{email}}</a>
  {% endfor %}
  {% else %}
  to-be-announced
  {% endif %}
  for more information.
</p>

<hr/>

{% if page.collaborative_notes %}
<h2 id="collaborative_notes">Collaborative Notes</h2>

<p>
We will use this <a href="{{ page.collaborative_notes }}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
<hr/>
{% endif %}

<h2 id="setup">Setup</h2>
<p>
  You will need the <a target="_blank" href="https://carpentries-incubator.github.io/python-intermediate-development-earth-sciences/setup.html">following software installed</a> and working correctly on your system to be able to follow the course.
</p>

<hr/>

<h2 id="material">Course Material</h2>
<p>
  <a target="_blank" href="https://carpentries-incubator.github.io/python-intermediate-development-earth-sciences/index.html">Course material</a> is available online.
</p>
<hr/>

{% commment %}
<h2 id="schedule">Schedule</h2>

The schedule below is approximate and subject to change.

{% include custom-schedule.html %}
{% endcommment %}
