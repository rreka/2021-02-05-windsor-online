---
layout: workshop      # DON'T CHANGE THIS.
# More detailed instructions (including how to fill these variables for an
# online workshop) are available at
# https://carpentries.github.io/workshop-template/customization/index.html
venue: "University of Windsor - Online"        # brief name of the institution that hosts the workshop without address (e.g., "Euphoric State University")
address: "online"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria"), videoconferencing URL, or 'online'
country: "ca"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1#Current_codes) for the institution that hosts the workshop
language: "en"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) for the
latitude: "45"        # decimal latitude of workshop venue (use https://www.latlong.net/)
longitude: "-1"       # decimal longitude of the workshop venue (use https://www.latlong.net)
humandate: "Feb 5, Feb 19 and Mar 2, 2021"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "9:30 am - 12:00 pm"    # human-readable times for the workshop (e.g., "9:00 am - 4:30 pm")
startdate: FIXME      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: FIXME        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Roger Reka"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["Mita Williams"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["roger.reka@uwindsor.ca"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes:  # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document (e.g., https://pad.carpentries.org/2015-01-01-euphoria)
eventbrite:           # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

{% comment %} See instructions in the comments below for how to edit specific sections of this workshop template. {% endcomment %}

{% comment %}
HEADER

Edit the values in the block above to be appropriate for your workshop.
If the value is not 'true', 'false', 'null', or a number, please use
double quotation marks around the value, unless specified otherwise.
And run 'make workshop-check' *before* committing to make sure that changes are good.
{% endcomment %}


{% comment %}
8< ============= For a workshop delete from here =============
For a workshop please delete the following block until the next dashed-line

8< ============================= until here ==================
{% endcomment %}


{% comment %}
Check DC curriculum
{% endcomment %}

{% if site.carpentry == "dc" %}
{% unless site.curriculum == "dc-ecology" or site.curriculum == "dc-genomics" or site.curriculum == "dc-socsci" or site.curriculum == "dc-geospatial" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Data Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>dc-ecology</code>, <code>dc-genomics</code>, <code>dc-socsci</code>, or <code>dc-geospatial</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% comment %}
Check SWC curriculum
{% endcomment %}

{% if site.carpentry == "swc" %}
{% unless site.curriculum == "swc-inflammation" or site.curriculum == "swc-gapminder" %}
<div class="alert alert-warning">
It looks like you are setting up a website for a Software Carpentry curriculum but you haven't specified the curriculum type in the <code>_config.yml</code> file (current value in <code>_config.yml</code>: "<strong>{{ site.curriculum }}</strong>", possible values: <code>swc-inflammation</code>, or <code>swc-gapminder</code>). After editing this file, you need to run <code>make serve</code> again to see the changes reflected.
</div>
{% endunless %}
{% endif %}

{% comment %}
EVENTBRITE

This block includes the Eventbrite registration widget if
'eventbrite' has been set in the header.  You can delete it if you
are not using Eventbrite, or leave it in, since it will not be
displayed if the 'eventbrite' field in the header is not set.
{% endcomment %}
{% if page.eventbrite %}
<strong>Some adblockers block the registration window. If you do not see the
  registration box below, please check your adblocker settings.</strong>
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="280px"
  scrolling="auto">
</iframe>
{% endif %}


<h2 id="general">General Information</h2>
<h3>Our workshop</h3>

{% comment %}
INTRODUCTION

Edit the general explanatory paragraph below if you want to change
the pitch.
{% endcomment %}
{% if site.carpentry == "swc" %}
{% include swc/intro.html %}
{% elsif site.carpentry == "dc" %}
{% include dc/intro.html %}
{% elsif site.carpentry == "lc" %}
{% include lc/intro.html %}
{% endif %}

<hr>
<h3>Details</h3>

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

{% comment %}
LOCATION

This block displays the address and links to maps showing directions
if the latitude and longitude of the workshop have been set.  You
can use https://itouchmap.com/latlong.html to find the lat/long of an
address.
{% endcomment %}
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
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latitude}}&mlon={{page.longitude}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latitude}},{{page.longitude}}">Google Maps</a>.
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

{% comment %}
DATE

This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
SPECIAL REQUIREMENTS

Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Requirements:</strong>
  {% if online == "false" %}
    Participants must bring a laptop with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% else %}
    Participants must have access to a computer with a
    Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) that they have administrative privileges on.
  {% endif %}
  They should have a few specific software packages installed (listed <a href="#setup">below</a>).
</p>


{% comment %}
CONTACT EMAIL ADDRESS

Display the contact email address set in the configuration file.
{% endcomment %}
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

<p id="roles">
  <strong>Roles:</strong>
  To learn more about the roles at the workshop (who will be doing what),
  refer to <a href="https://carpentries.org/workshop_faq/#what-are-the-roles-of-everyone-participating-in-a-workshop">our Workshop FAQ</a>.
</p>

{% comment %}
WHO CAN ATTEND?

If you would like to specify who can attend the workshop,
you can use the section below.

Move the 'endcomment' tag above the beginning of the following
<p> tag to make this section visible.

Edit the text to match who can attend the workshop. For instance:
- This workshop is open to affiliates to ABC university.
- This workshop is open to the public.
- If you are interested in attending this workshop, contact me@example.com
  for more information

<p id="who-can-attend">
    <strong>Who can attend?:</strong>
    This workshop is open to ....
</p>
{% endcomment %}

<hr/>

{% comment%}
CODE OF CONDUCT
{% endcomment %}
<h2 id="code-of-conduct">Code of Conduct</h2>

<p>
Everyone who participates in Carpentries activities is required to conform to the <a href="https://docs.carpentries.org/topic_folders/policies/code-of-conduct.html">Code of Conduct</a>. This document also outlines how to report an incident if needed.
</p>

<p class="text-center">
  <a href="https://goo.gl/forms/KoUfO53Za3apOuOK2">
    <button type="button" class="btn btn-info">Report a Code of Conduct Incident</button>
  </a>
</p>
<hr/>


{% comment %}
Collaborative Notes

If you want to use an Etherpad, go to

https://pad.carpentries.org/YYYY-MM-DD-site

where 'YYYY-MM-DD-site' is the identifier for your workshop,
e.g., '2015-06-10-esu'.

Note we also have a CodiMD (the open-source version of HackMD)
available at https://codimd.carpentries.org
{% endcomment %}
{% if page.collaborative_notes %}
<h2 id="collaborative_notes">Collaborative Notes</h2>

<p>
We will use this <a href="{{ page.collaborative_notes }}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
<hr/>
{% endif %}


{% comment %}
SURVEYS - DO NOT EDIT SURVEY LINKS
{% endcomment %}



{% comment %}
SCHEDULE

Show the workshop's schedule.

Small changes to the schedule can be made by modifying the
`schedule.html` found in the `_includes` folder for your
workshop type (`swc`, `lc`, or `dc`). Edit the items and
times in the table to match your plans. You may also want to
change 'Day 1' and 'Day 2' to be actual dates or days of the
week.

For larger changes, a blank template for a 4-day workshop
(useful for online teaching for instance) can be found in
`_includes/custom-schedule.html`. Add the times, and what
you will be teaching to this file. You may also want to add
rows to the table if you wish to break down the schedule
further. To use this custom schedule here, replace the block
of code below the Schedule `<h2>` header below with
`{% include custom-schedule.html %}`.
{% endcomment %}

<h2 id="schedule">Schedule</h2>






<div class="row">        <!-- first two days -->
  <div class="col-md-6"> <!-- left column -->
    <h3>Before the workshop</h3>
    <table class="table table-striped">
      <tr>               <!-- row 1   -->
        <td>Before starting</td>
        <td><a href="{{ site.pre_survey }}{{ site.github.project_title }}" target="_blank">Pre-workshop survey</a></td>
      </tr>
      <tr>               <!-- row 2   -->
        <td>Before starting</td>        <!-- time    -->
        <td>Install and verify that the software works</td>        <!-- content -->
      </tr>
      <tr>               <!-- row 3   -->
        <td>Wednesday, 10:00 am - 1:00 pm</td>        <!-- time    -->
        <td>(Optional) Drop-in installation help with Roger</td>        <!-- content -->
      </tr>
    </table>
  </div>
  <div class="col-md-6"> <!-- right column -->
    <h3>Session 1 (February 5, 2021)</h3>
    <h4>Getting started with R</h4>
    <table class="table table-striped">
      <tr>               <!-- row 1   -->
        <td>9:30 am</td>        <!-- time    -->
        <td>Introductions</td>        <!-- content -->
      </tr>
      <tr>               <!-- row 2   -->
        <td>9:45 am</td>        <!-- time    -->
        <td>How the workshop will work</td>        <!-- content -->
      </tr>
      <tr>               <!-- row 3   -->
        <td>10:00 am</td>        <!-- time    -->
        <td>R, RStudio and getting help</td>        <!-- content -->
      </tr>
      <tr>               <!-- row 3   -->
        <td>11:00 am</td>        <!-- time    -->
        <td>Break</td>        <!-- content -->
      </tr>
      <tr>               <!-- row 3   -->
        <td>11:20 am</td>        <!-- time    -->
        <td>Objects, vectors, data types & subsetting</td>        <!-- content -->
      </tr>
    </table>
  </div>
</div>
<div class="row">        <!-- days 3 and 4 -->
  <div class="col-md-6"> <!-- left column -->
    <h3>Session 2 (February 19, 2021)</h3>
    <h4>Working with data in R</h4>
    <table class="table table-striped">
      <tr>               <!-- row 1   -->
        <td>9:30 am</td>        <!-- time    -->
        <td>Loading data & data frames</td>        <!-- content -->
      </tr>
      <tr>               <!-- row 2   -->
        <td>10:30 am</td>        <!-- time    -->
        <td>Break</td>        <!-- content -->
      </tr>
      <tr>               <!-- row 3   -->
        <td>10:40 am</td>
        <td>Factors & formating dates</td>
      </tr>
      <tr>               <!-- row 3   -->
        <td>11:15 am</td>
        <td>Break</td>
      </tr>
      <tr>               <!-- row 3   -->
        <td>11:30 am</td>
        <td>dyplr and tidyr</td>
      </tr>
    </table>
  </div>
  <div class="col-md-6"> <!-- left column -->
    <h3>Session 3 (March 5, 2021)</h3>
    <h4>Data visualization in R</h4>
    <table class="table table-striped">
      <tr>               <!-- row 1   -->
        <td>9:30 am</td>        <!-- time    -->
        <td>Plotting with ggplot2</td>        <!-- content -->
      </tr>
      <tr>               <!-- row 2   -->
        <td>10:30 am</td>        <!-- time    -->
        <td>Break</td>        <!-- content -->
      </tr>
      <tr>               <!-- row 2   -->
        <td>10:50 am</td>        <!-- time    -->
        <td>Faceting, customization and exporting plots</td>        <!-- content -->
      </tr>
      <tr>               <!-- row 3   -->
        <td>End</td>
        <td><a href="{{ site.post_survey }}{{ site.github.project_title }}" target="_blank">Post-workshop survey</a></td>
      </tr>
    </table>
  </div>
</div>







<hr/>


{% comment %}
SETUP

Delete irrelevant sections from the setup instructions.  Each
section is inside a 'div' without any classes to make the beginning
and end easier to find.

This is the other place where people frequently make mistakes, so
please preview your site before committing, and make sure to run
'tools/check' as well.
{% endcomment %}

<h2 id="setup">Setup</h2>

<p>
  To participate in a
  {% if site.carpentry == "swc" %}
  Software Carpentry
  {% elsif site.carpentry == "dc" %}
  Data Carpentry
  {% elsif site.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  workshop,
  you will need access to the software described below.
  In addition, you will need an up-to-date web browser.
</p>
<p>
  We maintain a list of common issues that occur during installation as a reference for instructors
  that may be useful on the
  <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">Configuration Problems and Solutions wiki page</a>.
</p>

{% comment %}
For online workshops, the section below provides:
- installation instructions for the Zoom client
- recommendations for setting up Learners' workspace so they can follow along
  the instructions and the videoconferencing

If you do not use Zoom for your online workshop, edit the file
`_includes/install_instructions/videoconferencing.html`
to include the relevant installation instrucctions.
{% endcomment %}
{% if online != "false" %}
{% include install_instructions/videoconferencing.html %}
{% endif %}

{% comment %}
These are the installation instructions for the tools used
during the workshop.
{% endcomment %}

<h3>Install R and RStudio</h3>
<p>
  R and RStudio are two separate pieces of software:
  <ul>
    <li>
      <b>R</b> is a programming language that is especially powerful for data exploration, visualization, and statistical analysis
    </li>
    <li>
      <b>RStudio</b> is an integrated development environment (IDE) that makes using R easier. In this course we use RStudio to interact with R.
    </li>
  </ul>
  <div id="windows" class="section level5">
<h5 class="hasAnchor">Windows<a href="#windows" class="anchor-section"></a></h5>
<ul>
<li>Download R from the <a href="https://cran.r-project.org/bin/windows/base/release.htm">CRAN website</a>.</li>
<li>Run the <code>.exe</code> file that was just downloaded</li>
<li>Go to the <a href="https://www.rstudio.com/products/rstudio/download/#download">RStudio download page</a></li>
<li>Under <em>Installers</em> select <strong>RStudio x.yy.zzz - Windows Vista/7/8/10</strong> (where x, y, and z represent version numbers)</li>
<li>Double click the file to install it</li>
<li>Once it's installed, open RStudio to make sure it works and you don't get any error messages.</li>
</ul>
<div id="macos" class="section level5">
<h5 class="hasAnchor">MacOS<a href="#macos" class="anchor-section"></a></h5>
<ul>
<li>Download R from the <a href="https://cran.r-project.org/bin/macosx/">CRAN website</a>.</li>
<li>Select the <code>.pkg</code> file for the latest R version</li>
<li>Double click on the downloaded file to install R</li>
<li>It is also a good idea to install <a href="https://www.xquartz.org/">XQuartz</a> (needed by some packages)</li>
<li>Go to the <a href="https://www.rstudio.com/products/rstudio/download/#download">RStudio download page</a></li>
<li>Under <em>Installers</em> select <strong>RStudio x.yy.zzz - Mac OS X 10.6+ (64-bit)</strong> (where x, y, and z represent version numbers)</li>
<li>Double click the file to install RStudio</li>
<li>Once it's installed, open RStudio to make sure it works and you don't get any error messages.</li>
</ul>
</div>
<div id="linux" class="section level5">
<h5 class="hasAnchor">Linux<a href="#linux" class="anchor-section"></a></h5>
<ul>
<li>Follow the instructions for your distribution from <a href="https://cloud.r-project.org/bin/linux">CRAN</a>, they provide information to get the most recent version of R for common distributions. For most distributions, you could use your package manager (e.g., for Debian/Ubuntu run <code>sudo apt-get install r-base</code>, and for Fedora <code>sudo yum install R</code>), but we don't recommend this approach as the versions provided by this are usually out of date. In any case, make sure you have at least R 3.3.1.</li>
<li>Go to the <a href="https://www.rstudio.com/products/rstudio/download/#download">RStudio download page</a></li>
<li>Under <em>Installers</em> select the version that matches your distribution, and install it with your preferred method (e.g., with Debian/Ubuntu <code>sudo dpkg -i   rstudio-x.yy.zzz-amd64.deb</code> at the terminal).</li>
<li>Once it's installed, open RStudio to make sure it works and you don't get any error messages.</li>
</ul>
</div>
</div>
</p>

<div id="update-r-and-rstudio" class="section level3">
<div name="Update_R_and_RStudio" data-unique="Update_R_and_RStudio"></div>
  <h4 class="hasAnchor">Update R and RStudio<a href="#update-r-and-rstudio" class="anchor-section"></a></h4>
<p>If you already have R and RStudio installed, check if your R and RStudio are up to date:</p>
<ul>
<li>When you open RStudio your R version will be printed in the console on the bottom left. Alternatively, you can type <code>sessionInfo()</code> into the console. If your R version is 4.0.0 or later, you don't need to update R for this lesson. If your version of R is older than that, download and install the latest version of R from the R project website <a href="https://cran.r-project.org/bin/windows/base/">for Windows</a>, <a href="https://cran.r-project.org/bin/macosx/">for MacOS</a>, or <a href="https://cran.r-project.org/bin/linux/">for Linux</a></li>
<li>To update RStudio to the latest version, open RStudio and click on <code>Help" &gt; Check for updates</code>. If a new version is available, quit RStudio, follow the instruction on screen.</li>
</ul>
<p>Note: It is not necessary to remove old versions of R from your system, but if you wish to do so you can <a href="https://cran.r-project.org/bin/windows/base/rw-FAQ.html#How-do-I-UNinstall-R_003f">check here.</a></p>
</div>

<div id="install-required-r-packages" class="section level3">
<div name="Install_required_R_packages" data-unique="Install_required_R_packages"></div><h4 class="hasAnchor">Install required R packages<a href="#install-required-r-packages" class="anchor-section"></a></h4>
<p>During the course we will need a number of R packages. Packages contain useful R code written by other people. We will use the packages <code>tidyverse</code>, <code>hexbin</code>, and <code>patchwork</code>.</p>
<p>To try to install these packages, open RStudio and copy and paste the following command into the console window (look for a blinking cursor on the bottom left), then press the <kbd>Enter</kbd> (Windows and Linux) or <kbd>Return</kbd> (MacOS) to execute the command.</p>

<div><pre><code><span class="kw">install.packages</span>(<span class="kw">c</span>(<span class="st">"tidyverse"</span>, <span class="st">"hexbin"</span>, <span class="st">"patchwork"</span>))</code></pre></div>

<p>Alternatively, you can install the packages using RStudio's graphical user interface by going to <code>Tools &gt; Install Packages</code> and typing the names of the packages separated by a comma.</p>
<p>R tries to download and install the packages on your machine. When the installation has finished, you can try to load the packages by pasting the following code into the console:</p>
  
<div><pre><code><span class="kw">library</span>(tidyverse)
<span class="kw">library</span>(hexbin)
<span class="kw">library</span>(patchwork)</code></pre></div>

<p>If you do not see an error like <code>there is no package called ‘...’</code> you are good to go!</p>
</div>


