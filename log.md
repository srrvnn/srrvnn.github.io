---
layout: page
title: logs
heading: learning logs.
---

<div id="logs"> <div id="log"> it's either an emergency or something is wrong with the Google Sheets API. </div> </div>

<script>

// script to retreive what I am learning currently and display it on the page

var request = new XMLHttpRequest();
request.open('GET', 'https://spreadsheets.google.com/feeds/list/19w9sl1c9HuxkUeRkT7ThCQSfD-mjGTrm6FJE2B4hn6k/od6/public/values?alt=json', true);

request.onload = function() {
  if (request.status >= 200 && request.status < 400) {

    // Success!

    var data = JSON.parse(request.responseText);
    var logs = data.feed.entry;

    var elLogs = document.createElement('div');

    // iterate over links

    for (var i = logs.length-1; i >= 0; i--) {

      var elLog = document.createElement('div');

      var log = logs[i];

      var logLink = log.gsx$link.$t;
      var logTitle = log.gsx$title.$t;
      var logTime = String(log.gsx$date.$t).replace(/ at(.*)/, '');

      // create anchor tags

      var aLink = document.createElement('a');
      aLink.href = logLink;
      aLink.innerHTML = logTitle;
      aLink.className = 'mild';

      var spanTime = document.createElement('span');
      spanTime.innerHTML = logTime;

      // append them on the page

      elLog.className = 'log';
      elLog.appendChild(aLink);
      elLog.appendChild(spanTime);

      elLogs.appendChild(elLog);
    }

    document.querySelector('#logs').innerHTML = elLogs.innerHTML;

  } else {
    // We reached our target server, but it returned an error

  }
};

request.onerror = function() {
  // There was a connection error of some sort
};

request.send();

</script>
