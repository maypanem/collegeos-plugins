# CollegeOS for Claude

CollegeOS helps families compare US colleges and majors, keep their saved
choices in view, and continue a shared college application plan. This free
beta bundles two workflow skills with the CollegeOS connector. CollegeOS
charges no beta subscription fee; access to Claude and its plugin features
depends on your Claude plan.

## Who it is for

The plugin is for parents and guardians, and for students 18 or older. It is
not intended for users under 18. Most of the data it handles concerns a
student's college application, and that student may be a minor. The person
who connects chooses which student, if any, the connection may see.

## What it does

Before you sign in, CollegeOS answers public college questions with
source-backed facts about programs and related pathways, costs and application
requirements, with missing or dated information labeled as unknown. You can
start there without a CollegeOS account. When you want to keep the schools you
explored, CollegeOS gives you a review link that carries those choices into
account setup, where a person reviews and saves them.

After you sign in and choose a student, Claude can:

- read that student's saved shortlist, comparisons and deadlines, and, if you
  allow it, the family plan;
- compare two to four saved schools;
- suggest changes to the shortlist, school filters, active interests, the
  family's school portfolio or the next application action. A suggestion saves
  nothing: a family member reviews it in CollegeOS, and only the linked student
  can accept, edit or decline an application action;
- record progress the family reports on an action the student already
  accepted. This is saved directly, without a separate review step. CollegeOS
  attributes it to the signed-in person's role (student or parent) and keeps it
  marked as family-reported, never as a completed school requirement.

Some questions to start with:

- “My child likes robotics. Help us compare Texas A&M, CU Boulder, and UIUC.”
- “Show my student's shortlisted colleges.”
- “Continue our saved family plan and help us choose the next step.”

## Signing in and choosing what to share

Public questions need no sign-in. The first time you ask for saved family
information, Claude shows a Connect prompt. Sign in to CollegeOS, then on the
CollegeOS consent screen choose the student this connection may see and
whether it may work with the family plan. Connecting does not grant access to
every student or to future students, and it never includes essay text,
uploaded documents, transcripts or demographic answers.

You can see recent activity, change the students, turn off family-plan access,
or revoke the connection at any time in CollegeOS under **Settings → Connected
AI**. After you revoke it, CollegeOS stops answering the connection's requests
for student data. You can also disconnect in Claude's own settings.

## Data the connector reads and writes

The connector sends your request (school names, interests and, once you are
signed in, the student you chose) to `https://collegeos.app/api/claude/mcp`.
Results become part of your conversation with Claude, and Claude's own
policies apply to that conversation.

- **Reads**, only for the student you chose: account email, student display
  name, college lists and shortlists, any Explore view you choose to share,
  tier and admission-odds estimates, academic inputs (grades, test scores,
  course rigor), intended majors and interests, activities and awards,
  deadlines, and essay, recommender and checklist progress. With family-plan
  permission, also the accepted school portfolio and current action, pending
  revisions and recent family-reported progress.
- **Writes**: suggestions waiting for family review, kept as an attributed
  proposal history, and the family-reported progress records described above.
  The comparison panel is read-only.
- **Usage records**: CollegeOS logs each request from the connection (the tool
  used, the student involved, when it ran, how long it took and whether it
  succeeded) and records when the connection was last used.

CollegeOS keeps the connection and the students it may see until you delete
your CollegeOS account; revoking the connection stops its access immediately.
The usage log is kept for 180 days. Proposals and
reported progress are stored in your family's CollegeOS plan. The
[privacy policy](https://collegeos.app/privacy) has the full retention
schedule.

This bundle contains instructions and connection settings only. It has no
local program, hooks, embedded credentials or background collection, and it
sends data to no service other than the CollegeOS connector above. It does not
ask for essay text or uploaded documents. Other tools you use in the same
Claude conversation have their own permissions and policies.

## Accuracy and known limits

CollegeOS separates an interest such as robotics from a university's actual
degree offering and shows its sources and their dates. Admission estimates are
not guarantees, cost figures are not a personal aid offer, and personal target
dates are not official deadlines. CollegeOS does not submit applications.

- A comparison of several schools that needs fresh source data can take
  several minutes to return.
- Support for Claude Code and Cowork has not been verified yet. This section
  will say what works there once it has been tested.
- If Claude cannot show the visual comparison, it presents the same facts in
  text.

## Support, privacy and terms

For help, wrong facts, slow answers or confusing results, use the
[CollegeOS support page](https://collegeos.app/support). You can send a
message without signing in. Tell us that you used Claude, what you asked, what
happened and what you expected, and remove student names and other personal
details first.

- [Privacy policy](https://collegeos.app/privacy)
- [Terms of service](https://collegeos.app/terms)
