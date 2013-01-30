---
title: 'Software Managers, don&#8217;t forget to invest for the future!'
author: bsmith
layout: post
permalink: /2008/04/software-managers-dont-forget-to-invest-for-the-future/
categories:
  - Software
---
The following was seen recently, buried in the responsibilities list of an employment advertisement seeking a skilled Director of Software Engineering to lead a small team developing a new software product.

> Make time for continuous re-factoring and improving existing code and unit tests, to keep the codebase clean, maintainable and fun to work on 

What makes this so interesting to me is that there aren’t more senior level software engineering positions requiring this sort of investment in the organizations’ future. I really wish more companies would recognize that it is very important to aggressively carve out some fraction of the engineering time in each release and allocate it to re-factoring and improving existing code. 

Every place I work it seems like I end up being the sole voice for continuous improvement and refinement within the existing code. It always feels like I’m trying to sell snow removal equipment in the Middle East, or that I’m pushing 10 times my weight up a steep incline. 

Anyone who has spent time in *Startup Land* <sup>tm</sup> will be familiar with the oft-heard refrain “There isn’t time to do it right, just make it work.” This is destructive on so many levels; to the product, to the team, to the company, to share holder value, etc. 

The current mind set is basically to pour as many new features as possible in each subsequent product release and to fix some percentage of the bugs that exist in the system. When architectural deficiencies surface within the code-base management will often choose to defer addressing the issue (i.e., The issue is shelved indefinitely.) 

In essence this behavior is a race to the bottom, both for the development team and the product. As more features are added and more work-arounds are implemented to fix bugs the software becomes more and more brittle. This cycle continues until it is impossible to re-factor at all. The inevitable result is a full rewrite of the software or the death of the product as the company can no longer keep pace with newer competitors that are not constrained by this legacy. 

I once heard Grady Booch [[Blog][1], [Wikipedia][2]], co-inventor of UML, speaking at a conference about the state of our industry. He used the analogy of building dog houses vs. sky scrapers to make a similar point. His position was that without time spent on architecture, object-oriented design and continuous re-factoring it was impossible to build anything as complex as a sky scraper. He recognized that many teams have a grand vision for their software, but unless they embrace software architecture as a discipline they will never be able to stack up multiple dog houses to create a sky scraper. It just isn’t possible. I encourage you to read through his [PowerPoint presentation][3] on the topic or view a PDF [here][4]. 

A significant change in the mindset of software managers is needed in our industry. The lifespan of most successful large-scale software systems is at least 5 years, and many systems are in productive use for decades. To remain agile and responsive as a company the code-base must be re-factored, improved and refined at every step along the way.

<div class="addtoany_share_save_container">
  <div class="a2a_kit a2a_target addtoany_list" id="wpa2a_22">
    <a class="a2a_button_facebook" href="http://www.addtoany.com/add_to/facebook?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F04%2Fsoftware-managers-dont-forget-to-invest-for-the-future%2F&linkname=Software%20Managers%2C%20don%26%238217%3Bt%20forget%20to%20invest%20for%20the%20future%21" title="Facebook" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/facebook.png" width="16" height="16" alt="Facebook" /></a><a class="a2a_button_twitter" href="http://www.addtoany.com/add_to/twitter?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F04%2Fsoftware-managers-dont-forget-to-invest-for-the-future%2F&linkname=Software%20Managers%2C%20don%26%238217%3Bt%20forget%20to%20invest%20for%20the%20future%21" title="Twitter" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/twitter.png" width="16" height="16" alt="Twitter" /></a><a class="a2a_button_linkedin" href="http://www.addtoany.com/add_to/linkedin?linkurl=http%3A%2F%2Fwww.idevelopsoftware.com%2F2008%2F04%2Fsoftware-managers-dont-forget-to-invest-for-the-future%2F&linkname=Software%20Managers%2C%20don%26%238217%3Bt%20forget%20to%20invest%20for%20the%20future%21" title="LinkedIn" rel="nofollow" target="_blank"><img src="http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/icons/linkedin.png" width="16" height="16" alt="LinkedIn" /></a><a class="a2a_dd addtoany_share_save" href="http://www.addtoany.com/share_save" style="background:url(http://www.idevelopsoftware.com/wp-content/plugins/add-to-any/favicon.png) no-repeat scroll 9px 0px !important;padding:0 0 0 30px;display:inline-block;height:16px;line-height:16px;vertical-align:middle">More options</a>
  </div>
</div>

 [1]: http://www.booch.com/architecture/blog.jsp
 [2]: http://en.wikipedia.org/wiki/Grady_Booch
 [3]: http://www.booch.com/architecture/blog/artifacts/Software%20Architecture.ppt
 [4]: http://visitconsulting.net/UML.PDF