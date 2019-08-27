## Related work
{:#related_work}

The [Open Traffic Lights](https://opentrafficlights.org) (OTL) [](cite:cites vandevyvere_mepdaw_2019) project proposes a strategy for publishing traffic lights data in a semantically and technically interoperable way. Global identifiers (URIs) are defined with the OTL ontology for a subset of the terms of the currently used data standards SPAT and MAP. By agreeing on the semantics of these terms and applying RDF for describing facts, data publishers are not limited to the strict data structure in JSON format of SPAT and MAP. 
These standards propose the use of road lane connections instead of traffic lights to describe whether a road user can follow a certain direction. A traffic light represents multiple connections (e.g. you can turn right) that follow a certain [signal phase](https://w3id.org/opentrafficlights/thesauri/signalphase) and timing (SPAT) (e.g. you need to stop and wait for at least 5 seconds). Since most connections follow the same phase and timing, signal groups are introduced which represent the signal phase and timing of one or more connections. With MAP the geometry of the departure and arrival lane of a connection can be described. 
OTL also defines how the data can be published as time-sorted [Linked Data Fragments](https://brechtvdv.github.io/Article-Open-Traffic-Lights/#specification). This allows Web clients to not only retrieve the latest value of a signal group, but also its historic values through pagination links which can be used for predicting the signal phase duration of a signal group.

Predicting the phase duration has been done in related work [](cite:cites 8500307, 7013336) where tests have been run on traffic lights with a fixed cycle time. This means that a group of signal phases occur repeatedly between fixed time intervals. [Ibrahim et al.](cite:cites 8500307) propose a frequency distribution of phase durations for every signal phase and fixed cycle time, because an intersection can have a different fixed cycle time during working days than in the weekend. [Bodenheimer et al.](cite:cites 7013336) use graph transformations for representing the phase changes. For the prediction of the duration, they use timeslots of 15 minutes and different day classes (e.g. regular versus vacation day). The latter has been extended in [](cite:cites 7325247) for dynamic traffic lights and makes clear that prediction errors can be decreased significantly by having access to all detector information.

<!-- Using the cumulative frequency distribution also allows predicting with a fixed probability [](cite:cites 6965983). For example: when 10% of the historic phase durations happened before the predicted phase duration $$d_p$$, so $$F(d_p) = 0.1$$, then we can say with a probability of 90% ($$1-F(d_p)$$) that the real phase duration $$d$$ will take longer than $$d_p$$. -->

<!-- The idea is that historical values are a good reflection of future phases, so future phases will have a similar frequency distribution. The chance that a real phase duration will happen before the predicted duration corresponds with $$P(d≤d_p) = F(d_p)$$. 

For example: it is 90% sure that a phase will take longer when choosing a phase duration as prediction that corresponds with the first 10% of the cumulative frequency distribution.

the probability $$a$$ that the real phase duration $$d$$ takes longer than the predicted duration $$d_p$$ ($$a = P(d>d_p))$$). By taking the cumulative frequency distribution of phase durations $$F$$, then the chance that the . We can calculate $$a$$ by taking the reverse with the formula: $$a = 1-F(d_p)$$. This allows predicting with a fixed  -->