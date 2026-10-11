# CollegeOS for Claude

CollegeOS helps families compare college and major options, keep their saved
choices in view, and return to a shared application plan. This free beta bundles
two workflow skills with the CollegeOS connector. CollegeOS charges no beta
subscription fee; access to Claude and its plugin features depends on your
Claude plan.

Add the CollegeOS plugin in Claude, then use its Connectors tab to connect
CollegeOS when you want your saved family information. You can ask public
college questions first.

## Start with a question

- “My child likes robotics. Help us compare Texas A&M, CU Boulder, and UIUC.”
- “Show my student's shortlisted colleges.”
- “Continue our saved family plan and help us choose the next step.”

Public school exploration can begin without a CollegeOS account. When you want
to keep public choices, CollegeOS provides a review link that preserves them
through account setup. A person reviews and saves the portfolio in CollegeOS.

For saved family information, connect CollegeOS from this plugin's Connectors
tab and sign in. Select the student and permissions you want to share. Saved
facts, deadlines, and plan information use that authorized student scope.
Permission to read a plan is separate from permission to propose changes.

## Your choices stay under your control

The assistant can prepare changes for review. A proposal does not change the
saved shortlist, interests, or portfolio until the authorized person reviews it
in CollegeOS. Only the linked student can accept an application action. Progress
is recorded only after an explicit report on an accepted action and remains
family-reported. Connecting an account does not grant access to every student.

CollegeOS distinguishes an interest such as robotics from a university's actual
degree offering. It shows available sources and material uncertainty. Admissions
estimates are not guarantees; cost figures are not a personal aid offer. Some
facts may need current verification. If a visual comparison is unavailable in
your Claude surface, the assistant can present returned facts in text and use
the supplied CollegeOS review links.

## Data and feedback

The connector sends the requested school choices or authorized family questions
to `https://collegeos.app/api/family-guide/mcp`. Results become part of the
conversation with Claude. Authorized planning operations can store proposed
changes or reported progress in CollegeOS. This bundle contains instructions and
connection configuration only: it has no local executable, hooks, embedded
credentials, or background collection. It does not request essay prose or
uploaded documents. Other Claude tools used in a conversation have their own
permissions and policies.

Review the [CollegeOS privacy policy](https://collegeos.app/privacy) and
[service terms](https://collegeos.app/terms). Report wrong facts, confusing
results, or slow interactions through feedback in the CollegeOS web app. Include
the question and school names, and avoid pasting private family details into a
public issue. This beta will improve using customer feedback.
