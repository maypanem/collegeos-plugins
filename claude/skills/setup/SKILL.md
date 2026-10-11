---
name: setup
description: Help a family begin using CollegeOS after plugin setup, preserve public school choices into human review, or resume an existing saved plan.
---

Begin with the family's current question or choices. Do not restart an existing conversation's school intake. If schools or interests are missing, ask one short starting question to obtain only those required inputs. When the inputs are present and the family is new or asks an ordinary college question, call `public_college_guidance` before sign-in or full statistics and give a useful sourced answer. Ask only a decision-relevant unknown; if no question is supplied, briefly ask which schools or interests they want help with.

If choices already came from public guidance and the family asks to keep them, call `prepare_family_plan_review` with the returned exact `handoff_selection`, same nullable entry year and generated evidence question codes. The draft includes public IDs only. Give its exact review link. Ordinary email or Google signup/sign-in preserves the choices into human account/student setup and review; only the human saves. Do not auto-create an account, grant access, import personal conversation, accept a portfolio or report progress.

If the family asks to return to a saved plan, call `get_family_plan` with the student directly. If they ask for a saved shortlist or comparison, use `list_shortlisted_colleges` or one `open_comparison` directly. Use supported linking only when a private operation needs it; the person chooses the current student and explicit per-connection family-plan permission. Linking is separate from saving and actual student acceptance. On unavailable tools, denied access, cancellation or wrong account, explain the available review/recovery path and preserve current choices; never try another family scope.

Only the actual linked student can accept, edit or decline an action in CollegeOS. Suggestions stay proposed; progress needs an explicit report on an accepted action and remains family-reported. Never request skill installation, developer mode, tool names, unneeded intake or automatic all-student/writing grants. The CollegeOS workflow skill and endpoint instructions carry details for later decisions. Setup in a new or existing conversation must be tested in the actual host; this file alone does not prove activation or distribution.
