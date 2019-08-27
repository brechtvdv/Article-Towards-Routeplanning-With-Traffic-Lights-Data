<!-- <div class="printonly">This is a print-version of an article first written for the Web. The Web-version is available at <a href="https://brechtvdv.github.io/Article-Predicting-traffic-light-phases">https://brechtvdv.github.io/Article-Predicting-traffic-light-phases</a>.</div> -->

## Introduction
{:#introduction}

The city of Antwerp invested during 2018 in connecting the traffic lights of an intersection to the Internet. With the Open Traffic Lights project [](cite:cites vandevyvere_mepdaw_2019), the data about the phase and timing of these traffic lights have been made freely available on the Web as Linked Open Data. Typically, this is used for [Green Light Optimal Speed Advisory (GLOSA)](cite:cites 6799846) systems to save fuel through speed advice or count-down timer [](cite:cites dynamiceco). While GLOSA systems focus on the event of approaching an intersection, route planners have a more global view of the user journey where fuel savings can be one parameter. 
<span class="placeholder printonly">
<span style="display: block; height: 7em;"></span>
<!-- This is a dummy placeholder for the LNCS first page footnote -->
</span>
Implementing live changing data like these in traditional origin-destination route planning APIs would require much more complex tasks such as permanent tracking of the user.

Recently, work has been done on serverless route planning over [public transport timetables](cite:cites colpaert_icwe_2017) and [road networks](cite:cites colpaert_eswc_demo_2019) performing the route planning algorithm on the client-side. This appproach makes the client free to choose how it runs its route planning queries while data owners are only reponsible for publishing its data in an interoperable way. Such a client (cfr. [Planner.js](https://planner.js.org/)) can be extended to not only query over road networks, but also take traffic lights data into account. In the Netherlands and Belgium, dynamic traffic lights are installed which change their current phase duration according to detectors (pedestrian counters, cameras etc.). This introduces new challenges [](cite:cites spat_amsterdam), such as forecasting how long the current phase will likely take. In the Netherlands, opposed to the standard SPAT, it is [mandatory](https://smartmobilitycommunity.eu/sites/default/files/images/171116%20SPAT%20Profile%20v2.0%20%5BsubWG%20Dutch%20Profile%5D.docx) to calculate and publish this on the server-side, while in Belgium only the minimum and maximum duration is expected to be published.
In this article, we investigate how the current phase duration of the traffic lights in Antwerp can be predicted and demonstrate this on the client-side.