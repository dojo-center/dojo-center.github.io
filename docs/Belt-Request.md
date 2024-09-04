---
title: 'Belt Request'
layout: page
---
<div class="-alert alert-warning">
If this is your first time submitting a belt request, please visit the <a href="{{ '/Orientation-Request' | relative_url }}">Orientation Request</a> page for support.
</div>

Congratulations on making it to the point where you are considering making a belt claim!

Sometimes in our excitement we may have missed some of the signals and cues along the way.

## Insightful Learning Quality Check

Dialog is paramount to reinforce learning and is at the heart of the social connection of the Dojo Community.

Before working through the logistics of the belt claim, please ensure that you have found a Dialog Partner and upacked the concepts thoroughly.  Through this give and take we are challenged to recall what we have learned, test and deepen understanding.  Additionally, we increase awareness to consider how what we learn applies personally and in our social circles.

### Purposeful Reflection

The pull request will need to include a ***Purposeful Reflection***.

***Purposeful reflection illustrates key points of resonation from the content and dialog sessions through the learning progression.***

#### Guidance

{% assign beltLevel = site.beltLevels | where: "value", "green" | first %}
<img src="images/belt-{{beltLevel.value}}.png" height="50" alt="{{beltLevel.value}}" />
<a name="{{beltLevel.value}}-belt">{{beltLevel.label}}</a>

* Throw away or delete all of your stored notes
* Take a moment and center on the *Mission* and *Principles* of the domain
* Take a moment and center on the belt level competence guidance
* Time box creating your reflection (at least the first draft) to 30 minutes
* Describe:
  * 3 points of resonation
  * 3 points of struggle and how it was resolved
  * Overall experience with dialog sessions
  * Any story of how you have attempted to apply what has been learned
* Once you have submitted your belt claim, bring it up at the next Dojo Circle to be tested

{% assign beltLevel = site.beltLevels | where: "value", "red" | first %}
<img src="images/belt-{{beltLevel.value}}.png" height="50" alt="{{beltLevel.value}}" />
<a name="{{beltLevel.value}}-belt">{{beltLevel.label}}</a>

* Throw away or delete all of your stored notes
* Take a moment and center on the *Mission* and *Principles* of the domain
* Take a moment and center on the belt level competence guidance
* Draft a story:
  * Illustrating points of resonation and struggle with the Red level material
  * Display a clear and direct experiential shift in one of the key principles
  * Use storytelling directly, through fable or alternative
  * Capture the draft in the pull request
* Once you have a clear draft:
  * Review the story with 2 members of the community
  * Engage a Sensei to review, iterate and then publish to Medium, LinkedIn or another agreed location
  * Engage the current Cirlce leader to bring the claim up for demo testing at the next Circle
  * The story may or may not be read, but you will be expcted to respond to principle and curriculum based queries
    * Green and Red level concepts are in scope

{% assign beltLevel = site.beltLevels | where: "value", "black" | first %}
<img src="images/belt-{{beltLevel.value}}.png" height="50" alt="{{beltLevel.value}}" />
<a name="{{beltLevel.value}}-belt">{{beltLevel.label}}</a>

* Throw away or delete all of your stored notes
* Take a moment and center on the *Mission* and *Principles* of the domain
* Take a moment and center on the belt level competence guidance
* Draft a story:
  * Illustrating points of resonation and struggle with the Black level material
  * Display a clear and embodied understanding of each of the key principles and how they purposefully interrelate
  * Use storytelling directly, through fable or alternative
  * Capture the draft in the pull request
* Once you have a clear draft:
  * Review the story with 2 members of the community
  * Engage a Sensei to review, iterate and then publish to Medium, LinkedIn or another agreed location
  * Engage the current Cirlce leader to bring the claim up for demo testing at the next Circle
  * The story may or may not be read, but you will be expcted to respond to principle or curriculum based queries
    * Green, Red and Black level concepts are in scope

#### Belt Claim Review Criteria

During the review of the ***Belt Claim Pull Request*** the following criteria will be considered and labeled accordingly:

* Dialog
  * Sufficient: belt-claim-verified-dialog
  * Deficient: belt-claim-repeat-dialog
* Purposeful Reflection
  * Sufficient: belt-claim-verified-reflection
  * Deficient: belt-claim-expand-reflection
* Live Demo
  * Sufficient: belt-claim-verified-demo
  * Deficient: belt-claim-retest-demo 
* Formatting:
  * Sufficient: belt-claim-verified-formatting
  * Deficient: belt-claim-correct-formatting

If a Deficiency Flag (red label) appears, engage a Sensei to align on a path forward.

#### New Belt Claim

1. Open a web browser to the Members area of the Dojo GitHub repository:
    * [{{site.repositoryUrl}}/tree/main/docs/_data/members]({{site.repositoryUrl}}/tree/main/docs/_data/members)
1. Locate and open your file by your (hyphenated) name
1. Verify all information is correct, select Edit (top right), and add the new domain level claim request:

```yaml
---
name: Your Name
url: LinkedIn Url
inactive: false
belts:
  mindset: green
  agile: green
```

1. Enter "belt request" in the single line field underneath "Propose changes" near the bottom of the page
1. Submit the form by pressing the green "Propose Changes" button
1. The "Open a pull request" screen will open
1. In the large textarea provide your ***Recap and Purposeful Reflection*** of your experience and the belt claim
1. Press "Create pull request"
1. The pull request will be listed at [{{site.repositoryUrl}}/pulls]({{site.repositoryUrl}}/pulls)
1. A Sensei will respond as soon as practicable via email commententary with the pull request

