cloud.gov micro-purchase policies
========

This document provides an overview of how cloud.gov runs micro-purchases and a set of rules to which we will refer while running auctions. Pull requests to improve these rules are welcome.

How auctions work
-----------------

Most auctions follow a pretty standard process:

1.  **Pre-bidding period ("coming soon"):** Auctions are announced as a new issue in the `cg-product` repository before bidding begins. The issue will include "Auction (coming soon):" in the title, and refer to an open pull request detailing requirements. This gives prospective vendors time to estimate the effort that it might take to meet the acceptance criteria, and make suggestions on the pull request that would improve the deliverability of the auction or give a better result. To be notified of new auctions, vendors should use the GitHub "watch" function on the `cg-product` repository.
2.  **Bidding period ("open"):** Bidding opens when the pull-request is merged, and the issue title will be changed to include "Auction (open):". [Eligible](#eligibility-to-bid) vendors can place bids on the auction issue from the time it "opens" (its "opening date") until the time it "closes" (its "closing date"). At that time, the winner will be selected and must deliver the code by the auction's delivery deadline.
3.  **Delivery period:** The winning vendor indicates that they've begun work by [issuing a pull request](https://help.github.com/articles/using-pull-requests/), [referencing](https://guides.github.com/features/issues/#notifications) the issue associated with the auction, with "work-in-progress" in the title. At that point the conversation moves to the pull request itself (or others that are subsequently opened referencing the issue), wherein the winning vendor can update cloud.gov on their work in progress, ask questions, etc. Once the vendor believes their pull request meets the auction's acceptance criteria, they'll remove "work-in-progress" from the title of the pull request(s) and post on the auction issue to indicate they've finished their work. They can also request a review from the auctioneer (or a delegate) on the pull request(s) where they are delivering work.
4.  **Acceptance period:** cloud.gov evaluates the winning vendor's code against the auction's acceptance criteria. If the code meets the criteria, it's accepted. Otherwise, it's rejected.
5.  **Payment period:** If their solution is accepted, the winning vendor will [receive payment](getting-paid.md) at a payment URL they post in the issue since being declared the winner.

That's the process in a nutshell. Additional details, including deviations from this process, are covered below, under "source-selection method" and "delivery and acceptance policy."

Code of conduct
---------------

Micro-purchase bidders and awardees agree to abide by the [18F Code of Conduct](https://github.com/18F/code-of-conduct/blob/master/code-of-conduct.md). Violation of the code of conduct is grounds for rejection of any existing bid. Be kind to each other!

Transparency policy
-------------------

cloud.gov will publish, in a [publicly available website](https://github.com/18F/cg-product/tree/master/auctions), data associated with each auction (including the auction description, acceptance criteria, amendments, etc.) and other relevant information that is neither confidential or proprietary in nature nor source-selection sensitive information that would otherwise implicate procurement integrity concerns.

Auctions are run as a (standard) reverse-auction through a GitHub issue. Vendors place their bids by making posts to the issue. The (GitHub) identity of the vendor who placed it and the dollar amount of their bid will be publicly visible. Making this information public enables vendors to know if they are the low bidder and if they've been outbid.

Once a winner is chosen, cloud.gov will explicitly note the winner in the auction issue, and announce that bidding is closed.

During the delivery period of each auction, cloud.gov will collaborate with vendors in a publicly visible GitHub issue (or issues as needed) and/or pull request(s), sharing any data related to project management (for example, user stories, milestones, test scores, and performance metrics).

Premature closing
-----------------

cloud.gov reserves the right to delete an auction, prohibit bidding, and forego delivery at any point in the pre-bidding, bidding, delivery, and acceptance processes outlined above. cloud.gov will not issue payment to a vendor until that vendor's code has been deemed acceptable (see "Delivery and acceptance policy," below) and their pull request has been merged.

Eligibility to bid
------------------

In order to participate in auctions, vendors must 

- have a GitHub account
- [have a DUNS number](becoming-a-vendor.md)
- [register in SAM.gov](becoming-a-vendor.md)
- be able to accept payment via credit card

Bids above $10000 exceed the micro-purchase threshold that makes this lightweight process possible, and will be rejected.

Source-selection method
-----------------------

cloud.gov uses reverse-auctions to determine the source for any given procurement. Eligible vendors can place bids on an auction during its bidding period. Once that period ends, the winner will be selected by the auctioneer based on the best perceived combination of price and perceived risk, where evidence provided with the bid will be used to help assess risk. For example, a bidder may include with their bid a pointer to previously published work they completed which demonstrates they have the skills and knowledge to tackle the current work. This reduces the perceived risk that the bidder won't be able to deliver on the requirements.

In the event that a winner is either (a) unable to deliver on an auction by the delivery deadline assigned to them or (b) delivers code that is deemed unacceptable, cloud.gov reserves the right to reject the work, choose a new winner from previous bidders on the auction, or re-run the auction.

Bid acknowledgement and communication
-------------------------------------

cloud.gov will contact the winning bidder within 24 hours of the end of the auction. We require a timely response to acknowledge and confirm the bid amount.

Delivery and acceptance policy
------------------------------

cloud.gov gives every auction a **delivery period;** that is, a rough estimate of how long we think it'll take vendors to complete the work. If it's unspecified, the delivery period is one month.

An auction's **delivery deadline** is set whenever a winner is chosen. Delivery deadlines are based on an auction's delivery period, but exclude holidays and weekends.

We realize that unanticipated issues may arise during the delivery period that need to be resolved in order for winning vendors to successfully deliver. We encourage winning vendors to submit their work, even if it's incomplete, and ask questions early and often.

In some cases, cloud.gov may, at its discretion, agree to an extension of the delivery period, known as a "cure period." During the cure period, vendors are required to fix any bugs or otherwise refine their pull request so that it can be accepted and merged. The length of the cure period will vary depending on what is needed, but will not exceed five (5) business days.

Payment
-------

Payments are usually made promptly after winning vendor's pull request has been merged. Unless otherwise indicated in writing, payments will be made to the payment URL specified in the winning vendor's account using a government credit card. To ensure timely payment, vendors should specify their payment URL _before_ placing a bid. Any and all fees associated with the credit card payment are the responsibility of the winning vendor (that is, they will come out of the award).

