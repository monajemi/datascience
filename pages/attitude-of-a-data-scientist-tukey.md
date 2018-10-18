---
title: The attitude of a data scientist 
subtitle: By John Tukey
author: Hatef Monajemi
layout: page
hide: true

googlewebfonts: Gloria+Hallelujah
---

More than half a century ago in ["the future of data analysis"](https://projecteuclid.org/euclid.aoms/1177704711), John Tukey envisioned *a yet unrecognized field of science that is concerned with providing answers to realistic problems by means of experimentation, analysis of data, and judgements that may be guided by theory*. In 1962, he used *data analysis* to describe this field but today we can recognize it as *data science*. As part of his seminal paper, John lists what he thinks ought to be necessary attitudes for a data scientist. Since this is an important part of data science, I thought to share this part of John's paper with all data scientists out there. Also, because we are now in the "future" with respect to Tukey, I have taken the liberty of changing all occurances of 'data analysis' to 'data sience' in his original text. To see the original document: [`sed 's/data science/data analysis/gI'`](attitude-of-a-data-scientist-tukey-original).

<div style="background-color:rgba(255,255,255, 0.9); font-family:Times; text-align:left; vertical-align: middle; padding:30px;color:black;font-size:12;border-radius:10px;">
<p align="justify">
<b>What are the necessary attitudes?</b> Almost all the most vital attitudes
can be described in a type form: <em>willingness to face up to X.</em> Granted that facing
up can be uncomfortable, history suggests it is possible.
<br>    
We need to face up to <em>more realistic problems</em>. The fact that normal theory,
for instance, may offer the only framework in which some problem can be tackled
simply or algebraically may be a very good reason for starting with the <em>normal</em>
case, but never can be a good reason for STOPPING there. We must expect to
tackle more realistic problems than our teachers did, and expect our successors to
tackle problems which are more realistic than those we ourselves dared to take on.
<br>
We need to face up to the <em>necessarily approximate nature of useful results in
data science</em>. Our formal hypotheses and assumptions will never be broad
enough to encompass actual situations. Even results that pretend to be precise
in derivation will be approximate in application. Consequently we are likely
to find that results which are approximate in derivation or calculation will
prove no more approximate in application than those that <em>pretend</em> to be precise,
and even that some admittedly approximate results will prove to be closer
to fact in application than some supposedly exact results.
<br>
We need to face up to the need for <em>collecting the results of actual experience
with specific data-analytic techniques</em>. Mathematical or empirical-sampling studies
of the behavior of techniques in idealized situations have very great value, but
they cannot replace experience with the behaviour of techniques in real situations.   
<br>
We need to face up to the <em>need for iterative procedures in data science</em>. It is
nice to plan to make but a single analysis, to avoid finding that the results of
one analysis have led to a requirement for making a different one. It is also
nice to be able to carry out an individual analysis in a single straightforward
step, to avoid iteration and repeated computation. But it is not realistic to be
lieve that good data science is consistent with either of these niceties. As we
learn how to do better data science, computation will get more extensive,
rather than simpler, and reanalysis will become much more nearly the custom.
<br>
We need to face up to the <em>need for both indication and conclusion in the same
analysis</em>. Appearances which are not established as of definite sign, for example,
are not all of a muchness. Some are so weak as to be better forgotten, others
approach the borders of establishment so closely as warrant immediate and active following up. And the gap between what is required for an interesting indication and for a conclusion widens as the structure of the data becomes more complex.
<br>
We need to face up to the need for <em>a free use of ad hoc and informal procedures
in seeking indications</em>. At those times when our purpose is to ask the data what
it suggests or indicates it would be foolish to be bound by formalities, or by any
rules or principles beyond those shown by empirical experience to be helpful in
such situations.
<br>
We need to face up to the fact that, as we enter into new fields or study new
kinds of procedures, <em>it is natural for indication procedures to grow up before the
corresponding conclusion procedures do so</em>. In breaking new ground (new from
the point of view of data science), then, we must plan to learn to ask first of
the data what it suggests, leaving for later consideration the question of what it
establishes. This means that almost all considerations which explicitly involve
probability will enter at the later stage.
<br>
We must face up to the need for a <em>double standard in dealing with error rates,
whether significance levels or lacks of confidence</em>. As <em>students</em> and <em>developers</em> of
data science, we may find it worth while to be concerned about small difference
among error rates, perhaps with the fact that a nominal 5 % is really 4 % or 6 %,
or even with so trivial a difference as from 5 % to 4.5 % or 5.5 %. But as practitioners of data science we must take a much coarser attitude toward error
rates, one which may sometimes have difficulty distinguishing 1 % from 5 %,
one which is hardly ever able to distinguish more than one intermediate value
between these conventional levels. To be useful, a conclusion procedure need
not be precise. As working data scientists we need to recognize that this is so.
<br>
We must face up to the fact that, in any experimental science, <em>our certainty
about what will happen in a particular situation does not usualy come from directly
applicable experiments or theory</em>, but rather comes mainly through analogy be
tween situations which are <em>not known</em> to behave similarly. Data science has, of
necessity, to be an experimental science, and needs therefore to adopt the attitudes of experimental science. As a consequence our choices of analytical approach will usually be guided by what is known about simpler or similar situations, 
rather than by what is known about the situation at hand.   
<br>
Finally, we need to give up the vain hope that data science can be founded
upon a logico-deductive system like Euclidean plane geometry (or some form
of the propositional calculus) and to face up to the fact that <em>data science is intrinsically an empirical science</em>. Some may feel let down by this, may feel that
if data science cannot be a logico-deductive system, it inevitably falls to the
state of a crass technology. With them I cannot agree. It will still be true that
there will be aspects of data science well called technology, but there will also
be the hallmarks of stimulating science: intellectual adventure, demanding
calls upon insight, and a need to find out "how things really are" by investigation and the confrontation of insights with experience.
-- John Tukey (The Future of Data Analysis) with minor modification by Hatef Monajemi </p></div>
