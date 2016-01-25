---
layout: page
content: about
title: about @srrvnn
heading: about
---

saravanan is another guy with a computer who religiously believes in learning, creating, and happiness. he wants to solve every problem there is and he attempts to do it one commit at a time.

see him [code](http://github.com/srrvnn) &mdash; [tweet](http://twitter.com/@srrvnn) &mdash; [connect](http://linkedin.com/in/srrvnn). even better &mdash; [challenge](mailto:srrvnn@live.com?subject=Hello) his zero inbox strategy, or skim his &mdash; [resume](/resume).

<span class="mantra"> he lives by the mantra: <em> learn. rinse and repeat. </em> and is currently learning from <span id="link"></span>, and that was <span id="time"> </span>. </span>

<script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.10.2/moment.min.js"></script>
<script>

// script to retreive what I am learning currently and display it on the page

var request = new XMLHttpRequest();
request.open('GET', 'https://spreadsheets.google.com/feeds/list/19w9sl1c9HuxkUeRkT7ThCQSfD-mjGTrm6FJE2B4hn6k/od6/public/values?alt=json', true);

request.onload = function() {
  if (request.status >= 200 && request.status < 400) {

    // Success!

    var data = JSON.parse(request.responseText);

    // get the most recent link

    var mostRecentEntry = data.feed.entry.pop();
    var mostRecentLink = mostRecentEntry.gsx$link.$t;
    var mostRecentTitle = mostRecentEntry.gsx$title.$t;
    var mostRecentTime = String(mostRecentEntry.gsx$date.$t);

    // format the date to be parsed

    var timeIn24Hours = moment(mostRecentTime.match(/\d{2}:\d{2}[AP]M/)[0], ["h:mmA"]).format("HH:mm");
    mostRecentTime = mostRecentTime.replace(/(.*)at.*/, '$1' + timeIn24Hours);

    // get and calculate recency

    var mostRecentRecency = moment(mostRecentTime,'MMMM DD, YYYY HH:mm').fromNow();

    // create anchor tags

    var aLink = document.createElement('a');
    aLink.href = mostRecentLink;
    aLink.innerHTML = mostRecentTitle;
    aLink.className = 'mild';

    var aTime = document.createElement('a');
    aTime.href = '/log';
    aTime.innerHTML = mostRecentRecency;

    // append them on the page

    document.querySelector('#link').appendChild(aLink);
    document.querySelector('#time').appendChild(aTime);

    // fade in the learning intro

    document.querySelector('.mantra').style.transition = 'opacity 0.1s';
    document.querySelector('.mantra').style.opacity = 1;


  } else {

    // We reached our target server, but it returned an error

  }
};

request.onerror = function() {

  // There was a connection error of some sort
};

request.send();

</script>
