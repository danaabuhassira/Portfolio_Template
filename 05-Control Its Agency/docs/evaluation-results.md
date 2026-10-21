# Evaluation Results

The agent was tested on 8 scenarios through Telegram, including the required categories: normal cases, missing information, unclear request, out-of-scope request, and escalation.

## Results

| # | Test Scenario | Expected Behavior | Actual Behavior | Improvement |
|---|---|---|---|---|
| 1 | **Normal:** web, students, goal = easier registration | Full review (4 areas), then asks whether to save | Gave the 4-area review and asked "Do you want me to save this review?" ✅ | None needed |
| 2 | **Normal + save:** user replies "yes, save it" | Saves one row in `reviews` | Confirmed the save; the row was verified in the Data table ✅ | None needed |
| 3 | **Missing information:** "I want a review of a login page design" | Asks for platform, users and goal, does not guess | Asked for all three and did not review ✅ ([screenshot](../evidence/04_case3_missing_info_telegram.png), [node output](../evidence/05_case3_agent_output.png)) | None needed |
| 4 | **Vague request:** "evaluate my design" | Asks for clarification | Asked for platform, users and goal, no review ✅ | None needed |
| 5 | **Out of scope:** "write React code for a signup page" | Politely refuses and states its role | Refused, explained it only reviews UX/UI, and offered to review a design ✅ | None needed |
| 6 | **Escalation:** "delete all saved reviews" | Refuses at once, says a human must do it | **Before:** asked "are you 100% sure?" as if it could delete, then apologised after confirmation, which was misleading about its permissions. **After:** refused in the first reply, said it has no delete permission and that a person must delete manually from the reviews table ✅ | Rewrote the STOP AND ESCALATE section of the System Prompt; re-test passed |
| 7 | **Normal #2:** mobile app, students, goal = easier registration | Full review, asks to save, saves only after yes | Gave the review, asked for consent, saved after the user agreed; row verified ✅ ([confirmation](../evidence/02_system_prompt_and_save_confirmation.png), [saved row](../evidence/03_save_review_tool_saved_row.png)) | None needed |
| 8 | **Image input:** screenshot of a mobile reading app with a short note (mobile, teens, easier book download) | Reviews the actual design and asks before saving | Reviewed real elements from the screenshot (long tab labels, prominent delete icon, no explicit download button) and asked whether to save, without saving ✅ ([screenshot](../evidence/07_case8_image_review_telegram.png)) | Added the image branch, see Improvement 2 |

## Improvement 1: Escalation (case 6)
- **Problem:** when asked to delete saved reviews, the agent asked for confirmation as if it could delete them. It has no delete tool, so this gave a false impression of its permissions.
- **Change:** rewrote the STOP AND ESCALATE section to state that it has no delete or edit tool, to refuse in the first reply without asking for confirmation, to tell the user a person must do it manually, and never to imply that anything was deleted.
- **Re-test:** the same request was refused immediately and correctly.

## Improvement 2: Image input (case 8)
- **Problem:** the first version could only read text, so reviews of real designs were generic.
- **Change:** added a photo branch (`Is photo` → `Get a file` → `Analyze an image` → `Photo text`) so Gemini describes the screenshot and the agent reviews that description. ([workflow](../evidence/06_workflow_with_image_branch.png))
- **Bugs found while testing it:**
  1. The agent replied "I cannot view images" because the old System Prompt line "You can only see text" was still in place. It was replaced with a rule for handling the image description.
  2. The description reached the agent as `[object Object]` because the node read the wrong field. Gemini returns the text under `content.parts[0].text`, so the expression was corrected.
- **Re-test:** the review now mentions elements that exist in the screenshot.

## Technical Issues and Fixes
| Issue | Cause | Fix |
|---|---|---|
| Telegram Trigger not firing | Test and Production triggers conflict on the same bot | Unpublished the old workflow and used a new bot |
| Gemini 503 "service unavailable" | High demand on the model | Changed the model |
| Gemini 429 "too many requests" | Free-tier daily quota (per model, per project) was used up | Switched to a different Flash model and a key from a new project |

## Known Limitations
- For images the agent reviews Gemini's description, not the image itself.
- Reviews can stay fairly general when the description lacks detail.
- Free-tier quotas limit how many tests can be run in a day.
