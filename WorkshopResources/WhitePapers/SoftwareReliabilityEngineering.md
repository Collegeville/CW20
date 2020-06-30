# [SRE]+[UXDD] to Improve Productivity of Customer Support Processes

[Site reliability engineering (SRE)][SRE] is a term originally coined in 2002 by
engineering managers at Google to codify a particular set of software development
and support skills and practices associated with ensuring their software products
operate continuously and efficaciously. [SRE] as a discipline has gained widespread
adoption throughout the commercial software services industry.

[SaaP] readers who don't like or see how the word *site* applies should consider
a slight adaptation, *Software reliability engineering*. It is concerned with the
work involved in ensuring a deployed software product is and remains useable and
effective to its users and in responding to incidents relating to the use of the
software itself or some operational aspect of the computing enviornment in which
the software is being used.

While *Customer Support* is focused primarily on *responding to user inquiries*,
**Software** reliability engineering is focused on the continous investment of
effort and evolution of best practices to craft and carry out
*small corrective actions*, often in the form of improved automation, aimed at
continously improving the software and/or its processes and artifacts. This focus
and these activities represent a
[fusion](https://medium.com/@aHev/why-ux-researchers-should-learn-sre-practices-a2b213e69a8a>)
of aspects of Google's [Site Reliability Engineering][SRE] process (sometimes also
called
[Systems Reliability Engineering or Services Reliability Engineering](https://www.cio.com/article/3192531/why-you-need-a-systems-reliability-engineer.html))
and aspects of [User Experience Driven Development (UXDD)][UXDD]. That is
[SRE]+[UXDD]. However, *User Experience Driven* **Development** is a relatively new
term (not to be confused with *User Experience Driven* **Design**) where user
experience is being constantly fed back to inform development activities to
incrimentally improve the software. So, the remainder of this article uses [SRE]
as a shorthand for [SRE]+[UXDD].

Typically, [SRE] issues originate from users in the midst of using a software product
who are encountering some kind of difficulty. The work involved in handling
such inquiries should not end with addressing this one user's problem and sending
them on their way. When one user encounters a problem, others probably have or
will encounter the same problem. Furthermore, often the problems users encounter
are suggestive of minor, easily corrected deficiencies in either the software itself
or its associated processes and artifacts.

For mature DOE software projects with wide reach and many users, [SRE] activity
represents a brand of effort wholly different from conventional software product
development, planning and execution. Most DOE software projects have
no dedicated [SRE] resources. Instead, developers themselves must also support [SRE]
activity. Nonetheless, managing [SRE] work effectively and efficiently is an
essential part of ensuring positive
[outcomes for users](https://beyondphilosophy.com/15-statistics-that-should-change-the-business-world-but-havent).
In turn, this contributes to the productivity of both users and developers of the
software alike.

## The Basic Process and its Goals

[SRE] work is allocated and rotated among developers in *shifts*. During
a shift, one developer's [role](#roles) is to serve as the **Primary** contact.
S/he handles all user inquiries that come in during that shift. Except for
[escalations](#escalation), any other developers are free of [SRE]
responsibilities and can remain focused on planned software product
development work.

The [role](#roles) of the **Primary** is to [respond](#response_vs_resolution)
within the response time goal, to each inquiry. Ideally, all [SRE] activity during
a shift is handled and [resolved](#response_vs_resolution) solely by the
**Primary**. However, [escalations](#escalation), which should be rare, will
wind up engaging other developers. In addition, any active [SRE] issues that
remain unresolved at the end of a shift are formally handed off to the next
shift's **Primary**.

Active [SRE] issues are logged and tracked in an issue tracker separate from
the project's planned development. For any work the **Primary** performs, even if
it is a rather trivial amount of work to resolve, there should be an associated
[SRE] issue for tracking that work. Tracking even the trivial issues will help to
build a database to later mine to identify where further product or process
improvements can be made. Upon resolution of serious incidents, the
**Primary** prepares a brief *postmortem* to inform discussion at the next
project meeting of possible improvments in processes or practices.

Because [SRE] work tends to be [interrupt driven](#), there is always the chance
that the **Primary** will have no active issues. At these *idle* times, the
**Primary** uses their time to address *low-hanging fruit* type work. In
particular, there is no expectation that a developer serving as [SRE] **Primary**
can get any other work done beyond their active or idle [SRE] obligations. In slow
shifts, its conceivable they can. But, there can be no implied assumption or
expectation that this will be the case.

The **Primary** role is rotated so as to balance the load among team members.

### Goals

Some of the goals of [SRE] are...

* To build and maintain a reputation for timely and quality response to customer
  inquiries.
* To develop a practice of continuous user feedback and subsequent quality
  improvements to the software and associated processes and artifacts impacting user
  and/or developer productivity.
* To *load balance* [SRE] work in an equitable way across the development team.
* To reduce [SRE] interruptions for the team as a whole.
* To log, track and evolve a database of [SRE] activity and effort to help inform
  ongoing development plans and resource allocation.
* To identify and document escalation paths for major incidents.
* To ensure any previously agreed upon response time is met.

While many aspects of [SRE] are under the direct control of software developers,
some (those involving *operations* and the underlying computing infrastructure) are
not and involve collaboration with other teams in resolving. In most cases the
extent of the development team's involvement in resolving *operational* issues
is confined primarly to the software itself; its development, testing, release
and deployment which includes installations the team directly manages, hosted
binary downloads for common platforms and the tools and resources to build from
sources. Operational issues impacting software behavior but outside of this
scope are typically delegated to other teams who are responsible for the
associated processes and resources.

The preceding paragraphs describe [SRE] processes at a
basic level and in the ideal. Nonetheless, several terms here (those that are 
links or in *italics* in the paragraphs above) require elaboration. In addition,
there are also many practical matters which can serve to complicate the basic
process. These details are addressed in the remaining sections.

## [SRE] vs. Product Development

Part of the reason for formalizing these activities is the recognition of a
different category of work, [SRE], that is an essential part of maintaining
the overall quality of a software product as well as the productivity of both
developers and users of the software alike.  Nonetheless, this work is very
different from conventional *product development* type work where bug fixes,
feature enhancements, and technology refreshes are estimated and prioritized,
methodically planned and resources are allocated to meet target release dates.

Issues that impact one user's productivity often impact others. Likewise for
developers. When such issues come to a team's attention, whenever possible it
is often helpful to identify *two* kinds of actions; a short-term
*constructive* correction and a longer-term *comprehensive* solution.

|Constructive Correction|Comprehensive Solution|
|:---|:---|
|Short term|Longer term|
|Faster response|Slower response|
|Low cost/benefit|Higher cost/benefit|
|Low risk|Higher risk|
|Unplanned|Planned|
|Mitigation|Resolution|

A constructive correction has value only when...

* it represents a step towards the comprehensive solution,
* can sufficiently reduce the impact of the issue, and
* can be rolled out to users significantly sooner and with lower cost than the
  comprehensive solution.

Ordinarily, a constructive correction is something the
**Primary** handles as part of their [SRE] activity. The comprehensive solution,
which often involves more planning and resource allocation, is handled as part
of normal product development activities.

Constructive corrections can wind up falling through the cracks of traditional
software project management and planning processes. However, such work also often
represents low cost, high benefit improvements in quality of either the software
itself or the development or deployment processes supporting it. We refer to issues
of this nature as *low-hanging fruit* type issues.

Apart from acknowledging their existence, a key part of this process is the
allocation of a small fraction of resources for the sole purpose of supporting
[SRE] activities and developing a practice of continuously crafting constructive
corrective actions arising from [SRE] inquiries.

Consequently, another key role of the **Primary** is to use any time not working
active [SRE] issues to fix other *low-hanging fruit* issues from the
*product development* backlog. As a rule of thumb, low-hanging
fruit is considered to be anything that the team believes is fixable
within a half-day's (4 hours) worth of effort. When there are many such tasks in
the system to work on, the **Primary** is free to use his/her judgment to decide
which s/he can most productively address.

## Response Time and Response vs. Resolution

It is important to distinguish between *response* and *resolution* of [SRE] incidents.
A key goal in this process is to ensure that customer inquiries do not go
unanswered. However, *responding* to an [SRE] inquiry does
not necessarily mean *resolving* it. Sometimes, the only response possible is to
acknowledge the inquiry and let the user know that the resources to
address it will be allocated as soon as practical. In many cases, an *immediate*
response to acknowledge even just the receipt of a user's inquiry with no
progress towards actual resolution goes a long way towards creating the goodwill
necessary to negotiate the time to respond more fully.

*Resolution* of an [SRE] issue often involves one or more of the
following activities...

  * Answering a question or referring a user to documentation.
  * Diagnosing the issue.
  * Developing a work-around for users.
  * Developing a reproducer for developers.

    * This may include any relevant user data files as well as approval, where
      appropriate for world read access to such data as part of attaching to
      a GitHub issue.

  * Identifying any *low-hanging fruit* type work that would address, even if
    only in part, the original [SRE] inquiry and then engaging in the
    work to resolve it.
  * Determining if the user's issue is known (e.g. an issue ticket already exists).
  * Updating a known issue with new information from this user, perhaps
    adjusting labels on the issue or putting the issue back into the
    un-reviewed state for further discussion at a project meeting.
  * Identifying and filing a new *product development* type issue.

To emphasize the last bullet, *resolution* does not always mean a user's
issue can be addressed to *satisfaction* within the constraints of the [SRE]
process as it is defined here. Sometimes, the most that can be achieved is
filing a highly informative issue to be prioritized, scheduled and
ultimately resolved as part of normal product development activities.
The [SRE] issue gets *promoted* to a product development issue. It is closed
in the [SRE] issue tracker and new issue is opened in the product development
issue tracker including a reference to the original [SRE] issue. Doing so does
serve to *resolve* the original [SRE] issue that initiated the work.

## Escalation, Serious Incidents and Postmortems

[SRE] inquiries may escalate for a variety of reasons. The 
technical expertise or authority required to respond to a given inquiry may be
beyond the **Primary**'s abilities or other difficulties may arise. For issues
that the **Primary** does not quickly see a path to resolution, other developers
may be enlisted. However, where a **Primary** is responsible for maintaining the 
response time goal, other developers so enlisted are free to either delay or even
decline to respond (but nonetheless inform the **Primary** of this need) if their
schedule does not permit timely response. Such a situation could mean that the
only remaining course of action for the **Primary** to *resolve* the issue is to
file a product development issue as discussed at the end of a preceding section.

If after investigation and diagnosis, the work required to resolve an [SRE]
incident remains highly uncertain or is not believed to be a
*low-hanging-fruit* type task, the **Primary** should search the product
development issues to see if there is a known issue and, if so, add additional
information from this new [SRE] incident or submit a *new* issue to the product
development issue tracker. Such action then *resolves* the original [SRE] issue.

Serious incidents are those that have significant productivity consequences for
multiple users and/or require an inordinate amount of resources (either time or
people or both) to diagnose, work-around and/or ultimately properly correct.

When such incidents occur, it is a best practice to spend some time considering
adjustments in processes that can help to avoid repeating similar issues in
the future.

When such incidents reach [SRE] resolution, the **Primary** prepares a
brief *postmortem* (often just a set of bullet points) explaining what happened
and why, estimating the amount of resources that were needed to resolve the
incident, describing key milestones in the work to resolve the incident and
suggesting recommendations for changes in processes to prevent such incidents
from being repeated. This *postmortem* will be used to guide team discussion
during a subsequent project meeting.

## Managing [SRE] Effort and Costs

The key parameters in these processes is the *coverage* of support hours, the
response time and the length of a *shift*. In the IT world where companies like
Google, Apple and Amazon have whole teams dedicated to [SRE] activity, coverage
is 24/7, response time is measured in minutes and shifts are weeks or months.

For a DOE software project of moderate size (say 6 or more developers) *and*
which has a sufficiently large user base, coverage should be during
*normal business hours*, response time should be about a half-day (4 hours) and
shift length should be about one week. For a project of this size, if a
**Primary** is wholly consumed with [SRE] activities during their shift, this
would represent about 17% of the project's development resources.

If this is too much, the solution is to reduce coverage, either shorter days or
fewer days. For example, maybe the project decides coverage will be normal
business hours but only Monday through Wednesday. This reduces the *maximal*
cost for [SRE] activity from 17% to a more manageable 10%. In this example, it
may make sense to lengthen a shift to two weeks.

For even smaller projects or projects with few users, it may be
appropriate to reduce coverage to only certain days out of a month and a shift
length of a day. In such cases the goal of ensuring a *response time* becomse
inapplicable. There is simply not enough resource available to ensure any
specific response time. Nonetheless, as long as expectations are appropriately
set, users will often demonstrate surprising patience and understanding.

### Load Balancing [SRE] Effort

To balance [SRE] work load among developers, the **Primary** role is rotated.
However, a number of factors can complicate a simple round-robin
approach including percent-time assignments of team members, alternate work schedules,
working remotely, travel, vacations, multi-day trainings, etc.

Round-robin assignment may lead to a fair load by head-count but isn't weighted by
percent-time assignments. From a percent-time assignment perspective, it might be
more appropriate for a 50% time developer to serve as **Primary** only half as often
as a 100% time developer.

For teams where a majority of developers divide their time across multiple
projects, it may make sense to use 50% as the *nominal* developer assignment.
The aim is an approximately round-robin load balance where contributors who are
more than 50% time are occasionally assigned an extra shift.

### Handoffs

These [SRE] processes involve two kinds of *handoffs*. One is the
redirection of a customer who makes first contact with a developer not serving as
the **Primary**. The other is the handoff of unresolved [SRE] issues
from one shift's **Primary** to the next.

To handle customer redirection handoffs, it is a best practice to use a three-way
handoff giving the customer some assurance that their initial contact with someone
is successfully handed off to the **Primary**. For example, for a call-in, it
is a best practice to try a three-way call transfer. For some developers, the
prospect of redirecting friends and colleagues with whom they may have long
standing relationships may be initially uncomfortable. But it is important to
recognize that this an essential part of achieving various of the goals of this
process, such as reducing [SRE] interruptions for the team as a whole and tracking
[SRE] effort.

If an active [SRE] issue cannot be resolved within the shift of
a **Primary**'s assignment, it gets handed off to the next shift's **Primary**.
Such handoffs are managed formally with a comment (or email) to the
customer(s) and the next shifts's **Primary** in the associated
issue. The associated issue(s) in the [SRE] issue tracker
is re-assigned by the outgoing **Primary** upon ending
their shift. However, an outgoing **Primary** may be near enough
resolving an [SRE] issue that it makes more sense for him/her to carry it completion
rather than hand it off.

## Supported Communication Platforms

An [SRE] inquiry with the team begins with a *first contact* and may optionally
be followed by *ongoing* conversation. These two phases of communication have different
requirements and can involve different processes. This is due to the need
to balance two priorities; *accessibility* for users and *productivity* for developers.

To maximize accessibility for users, supporting a wide variety of
[communication *platforms*](https://www.elcom.com.au/resources/blog/15-essential-communication-platforms-and-software-to-use)
for first contact is desireable. However, to maximize productivity for developers,
the platform(s) used for ongoing conversations must be restricted.

Users who are co-located with the development team can often spontaneously make
first contact with a developer by an office drop-in or a tackle in the hallway or
parking lot. The virtual equivalent of this occurs even more frequently on various
communcation platforms such as Confluence, Jabber, MS Teams, etc. where users can
wind up engaging specific developers that happen, by nothing more than coincidence,
to also be using those platforms.

A challenge with spontaneous first contacts is that they inadvertently
single out a specific developer who is then expected to at least *respond* and
possibly even to also *resolve* the issue. But, these actions and the effort they
involve are the responsibility of the [SRE] **Primary**. Consequently, spontaneous
first contacts can wind up jeopardizing the goals of [SRE] processes by making it
difficult to track, allocate and manage [SRE] effort.

Therefore, officially supported platforms for first contact should be those which
engage the *whole team* instead of singling out a specific member (e.g. Email
list or GitHub conversation). Whenever users attempt a first contact through
something other than a supported platform, the receiving developer should make an
effort to hand-off the inquiry to the **Primary** [SRE] as quickly and politely as
practical.

What does it mean for a platform to be *supported*? It means
there is an *assurance* that it is being *monitored* by the [SRE] **Primary**.
In addition, supported platforms are encouraged and promoted in any documentation
where support processes are described.

Balancing the priorites of user accessibility with developer productivity
involves a compromise on the number of platforms a team can make an assurance
to monitor. However, the approved platforms should be periodically reevaluated. If
there is some platform which seems to be gaining popularity among users, it may
make sense to include it as a supported platforms.

## A Common Misconception: [SRE] is an Interruption to Product Development

There are several advantages in having all team members participate in and
gain [SRE] experience. These include...

  * Learning what problems users are using the package to solve.
  * Learning how users use the package.
  * Learning what users find easy and hard about the package.
  * Learning where documentation and/or interfaces needs improvement.
  * Learning operational aspects of user's work that the package can impact.
  * Building collaborative relationships with users.

When faced with a long backlog of product development tasks, team members can
all too easily perceive [SRE] work as an *interruption* to those tasks.
This is a common and serious misconception.

Software Reliability Engineering is an important aspect to a successful product
and project on par with any other major development work. It is part of what is
involved in maintaining and improving the productivity of the software for
developers and the utility of the software for users.

[SRE]: https://landing.google.com/sre/sre-book/toc/ "Google's on-line book on Site Reliability Engineering"
[UXDD]: https://www.microsoftpressstore.com/articles/article.aspx?p=2492952&seqNum=3 "User Experience Driven Design"
[SaaP]: https://en.wikipedia.org/wiki/Software_as_a_Product "Software as a Product"

https://medium.com/@carlosjoel.tavares_25618/ux-driven-development-9a35cee2c3b1
