#### Financially Reimbursed Open-source Gig Support

* **Financially Reimbursed:** Whatever the implementation (spam prevention & corporate feature requests should probably be handled differently), we need a way to show that we value our open-source maintainers & there is no more authentic way to do that than through money.
* **Open-source:** I needed a vowel & we’re talking about open-source here. I’m open to alternative vowels. 😂
* **Gig:** Maintainers have gotten used to being taken for granted. Fuck that. Open-source contributions should be treated as optional gigs in order to rebalance the expectations of the Cloud Native Computing Foundation community. Maintainers who do not value themselves appropriately risk burnout, either through willpower exhaustion or demand overwhelm.
* **Support:** We need to acknowledge how important open-source support is, as the rate of technological churn continues to increase. Open-source software is great. Open-source software that is maintained against bit-rot is even better.

#### FROGS implementation through a bounty system

* When a Pull Request, Feature Request, Bug Report (UX or security) is initially created, the creator can submit funds towards the completion of the created item (the "general task")
* After a bounty target is created, a contributor provides an estimate for the cost of initial review
* Once a review bounty has been created, sponsors can submit funds towards either the review task (a "specific effort") or the completion of the general task
* After a review is completed, contributors may create estimates for resolving review comments
* Sponsors submitting funds targeting specific efforts may specify if they wish for their funds to be refunded or rolled-over to the general task should the bounty be nullified
* Any changes made by the creator of the general task will trigger a new pending review estimate & a pending manual nullification check for existing bounties
* Sponsors submitting funds targeting specific efforts will have to validate bounty fulfillment before funds release
* Contributors may target general task funds to specific effort bounties or designate a split of funds to multiple contributors upon general task completion
* Any specific effort bounties pending will be refunded upon general task completion

#### Process Design by Contract (WIP - Doesn't currently match natural language specification above)

CRUD Resources:
* Contributors
* Collaboration Platforms
* Escrow Systems (This entire thing succeeds or fails on finding multiple credible, easy to use escrow systems)

Bounty Creation:
* Prerequisites:
  * Target: Reference to a Pull Request, Feature Request, Bug Report (UX or security)
  * Estimate: Cost estimate of effort
* Postconditions:
  * Bounty (linked to specific, immutable effort request by commit, time-stamp, etc) is posted on the collaboration platform, likely in the general task's activity feed
* Failure Condition
  * Contributor is notified of contribution failure & reason

Bounty Contribution:
* Prerequisites:
  * Intent: Reference to an existing bounty (specific) or general task
  * Bid: Sponsor claims they have X amount of money available
  * Rollover or Refund: Sponsor's choice if targeting a specific effort
* Postconditions:
  * X amount of funds are transferred from bounty creator to escrow account
  * Conditions are set within escrow system for release of X amount of funds
* Failure Condition
  * Sponsor is notified of contribution failure & reason

Bounty Reward:
* Prerequisites:
  * one or more contributor(s) satisfies bounty Y conditions
  * escrow system Z has registered release conditions for bounty Y
  * escrow system Z has funds available to fulfill for bounty Y
  * escrow system Z has financial reference for contributor(s)
  * escrow system is informed of release condition satisfaction through collaboration platform webhook
* Postconditions:
  * X amount of funds are transferred from escrow account to contributor(s)
  * Any funds targeting bounty Y beyond the range of the registered release conditions are refunded
* Failure Condition
  * Everyone? is notified of contribution failure & reason

Universal Prerequisites (UP): There must be at least one of each of the CRUD resources above
Universal Invariant:
* Specifications currently assume that contributors are always in consensus
* Any bounty created through a escrow system is dependent on the existence of that escrow system (TODO: create a fallback system for an escrow system failure)
* All the CRUD resources in the UP must exist throughout any process for said process to succeed.

Inspired by https://judahmeek.com/p/we-need-frogs-to-defend-foss
