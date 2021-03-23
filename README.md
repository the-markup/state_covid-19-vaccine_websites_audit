# State COVID-19 Vaccine Website Analysis

This is the data used for our story "[We Ran Tests on Every State’s COVID-19 Vaccine Website](https://themarkup.org/TKTK)."

We looked at the vaccine finder pages for all 50 states plus Puerto Rico and Washington, D.C. We wanted to find out more about the web infrastructure used by each site. We started with a list of state vaccine pages listed by the [Department of Health and Human Services](https://www.vaccines.gov/get-vaccinated). In some cases we chose a more specific page where a user would be able to locate a vaccination.

We looked at three areas:

- Privacy and tracking
- Performance
- Accessibility

## Privacy and tracking

We used The Markup's own privacy inspector, [Blacklight](https://themarkup.org/blacklight), to analyze these sites. Blacklight performs seven tests looking for specific user-tracking technologies.

You can read the methodology for Blacklight [here](https://themarkup.org/blacklight/2020/09/22/how-we-built-a-real-time-privacy-inspector). 

- Ad trackers
- Third party cookies
- Web fingerprinting
- Session recording
- Keystroke logging
- Facebook tracking pixel
- Google Analytics

We also captured the raw HAR file from the Blacklight analysis, which includes a record of all requests needed to display the website. 

## Performance and Accessibility

We wanted to record some measure of technical quality for these sites, which translates into a real-world impact on users searching for a life-saving vaccine, with each state having a different set of rules and technical infrastructure.

We used Google's widely used [Lighthouse](https://developers.google.com/web/tools/lighthouse#cli) website testing suite to analyze these sites, and we chose three of the many audits available in the tool:

- [Performance](https://web.dev/lighthouse-performance/): A general purpose test measuring how long it takes until a page has loaded and can be used. This returns a weighted percentage score between 0 and 100, with 100 being the best.  

- [Accessibility](https://web.dev/lighthouse-accessibility/): This test measures which technologies have been used to help make the page more accessible to users with disabilities and people who may be using assistive technology like screen readers to access the site. The Americans with Disabilities Act requires websites to accommodate disabled users, and these scores help determine what improvements could be made. This returns a weighted percentage score between 0 and 100, with 100 being the best.

## Testing
Website testing can vary greatly as there are so many factors that can affect the results, such as network congestion, web infrastructure availability, and other issues. To correct for this, we ran the tests in three sessions, from three locations in the U.S. at three different times. Each test session ran the Lighthouse tests 10 times in a row for each state. We use the mean score for all 30 tests per state. All testing was for the mobile version of these websites. 

- Test session 1 - March 19, 2021 4 P.M. - 8 P.M EDT. - Greater New York City Area, NY 
- Test session 2 - March 20, 2021 3 A.M. - 9:30 A.M. EDT - Los Angeles, CA (via VPN)
- Test session 3 - March 20, 2021 11 A.M. - 5:30 P.M. EDT - Dallas, Texas (via VPN)

## Data
[state_vaccine_websites.csv](https://github.com/the-markup/state_covid-19-vaccine_websites_audit/blob/main/state_vaccine_websites.csv) - *33 KB. 53 rows. First row is the header*.

[screenshots/](https://github.com/the-markup/state_covid-19-vaccine_websites_audit/tree/main/screenshots) - A collection of each site's mobile screenshot captured by Blacklight. 52 JPEG files. 1125 x 2436 pixels @ 72dpi. 

## Data Dictionary 
												

<table border="0" class="dataframe">
  <thead>
    <tr style="text-align: left;">
      <th>Column</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>state</strong></td>
      <td>The postal abbreviation for the state / territory / district that runs the vaccination page.</td>
    </tr>
    <tr>
      <td><strong>state_long</strong></td>
      <td>The state / territory / district that runs the vaccination page.</td>
    </tr>
     <tr>
      <td><strong>url</strong></td>
      <td>The URL of the vaccination page. </td>
    </tr>
     <tr>
      <td><strong>perf_mean</strong></td>
      <td>The average Lighthouse Performance score.</td>
    </tr>
     <tr>
      <td><strong>perf_sd</strong></td>
      <td>The standard deviation for the Lighthouse Performance scores.</td>
    </tr>
     <tr>
      <td><strong>access_mean</strong></td>
      <td>The average Lighthouse Accessibility score.</td>
    </tr>
     <tr>
      <td><strong>access_sd</strong></td>
      <td>The standard deviation for the Lighthouse Accessibility scores.</td>
    </tr>
        <tr>
      <td><strong>cookies</strong></td>
      <td>The Blacklight third-party cookies test. The number of third-party cookies found.<a href='https://themarkup.org/blacklight/2020/09/22/how-we-built-a-real-time-privacy-inspector#third-party-cookies'>Read more here</a>.</td>
    </tr>
        <tr>
      <td><strong>ddg_join_ads</strong></td>
      <td>The Blacklight ad trackers test. The number of ad trackers found. <a href='https://themarkup.org/blacklight/2020/09/22/how-we-built-a-real-time-privacy-inspector#ad-trackers'>Read more here</a>.</td>
    </tr>
        <tr>
      <td><strong>canvas_fingerprinters</strong></td>
      <td>The Blacklight canvas fingerprinting test. 0=not detected, 1=detected. <a href='https://themarkup.org/blacklight/2020/09/22/how-we-built-a-real-time-privacy-inspector#canvas-fingerprinting'>Read more here</a>.</td>
    </tr>
        <tr>
      <td><strong>fb_pixel_events</strong></td>
      <td>The Blacklight canvas fingerprinting test. 0=not detected, 1=detected. <a href='https://themarkup.org/blacklight/2020/09/22/how-we-built-a-real-time-privacy-inspector#facebook-pixel'>Read more here</a>. </td>
    </tr>
        <tr>
      <td><strong>ga</strong></td>
      <td>The Blacklight Google Analytics “Remarketing Audiences” test. 0=not detected, 1=detected. <a href='https://themarkup.org/blacklight/2020/09/22/how-we-built-a-real-time-privacy-inspector#google-analytics-remarketing-audiences'>Read more here</a>.</td>
    </tr>
    <tr>
        <td><strong>key_logging</strong></td>
      <td>The Blacklight keystroke logging test. 0=not detected, 1=detected. <a href='https://themarkup.org/blacklight/2020/09/22/how-we-built-a-real-time-privacy-inspector#key-logging'>Read more here</a>.</td>
    </tr>
    <tr>
        <td><strong>session_recorders</strong></td>
      <td>The Blacklight session recording test. 0=not detected, 1=detected. <a href='https://themarkup.org/blacklight/2020/09/22/how-we-built-a-real-time-privacy-inspector#session-recording'>Read more here</a>.</td>
    </tr>    
  </tbody>
</table>


## Limitations

Website testing is dependent upon a huge number of variables, including network congestion, web service availability, the state of the computer running the tests, and many other factors. 

Using a VPN for the tests in other cities is not a perfect way to test for geographic differences in test results. 
Read the full methodology for Blacklight, along with its own limitations [here](https://themarkup.org/blacklight/2020/09/22/how-we-built-a-real-time-privacy-inspector#limitations). 

There are limitations to Lighthouse’s [performance](https://web.dev/performance-scoring/) and [accessibility](https://web.dev/accessibility-scoring/) audits, which you can read about in detail [here](https://web.dev/learn/#lighthouse). 

## Licensing
Copyright 2021, The Markup News Inc.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

3. Neither the name of the copyright holder nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
