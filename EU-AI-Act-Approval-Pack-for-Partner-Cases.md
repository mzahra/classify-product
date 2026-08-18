# EU AI Act Approval Pack, Consulting Review of Partner Cases

Prepared by: Zahra Moghaddasi
Client cases reviewed: 4
Scope: This pack answers one question for each proposal, "Can we launch this?"

## Executive summary

I reviewed four AI proposals from four different organizations: a manufacturer, a hospital, an insurance company, and a school district. One system is safe to approve as is. One is high-risk and needs formal documentation and real human oversight before launch, not just a formality review step. One is low risk but currently missing a required disclosure, a simple fix. One, as currently designed, is not lawful and must be redesigned before it can move forward. None of the four are technically complex, the biggest gaps across the board are role clarity (who is the provider, who is the deployer), honest naming of what the system actually does, and whether a human decision is real or just a rubber stamp.

At a glance:

| Case | Client | Category | Decision |
|---|---|---|---|
| 1 | Manufacturer, predictive maintenance | Minimal risk | Approve |
| 2 | Hospital, emergency triage | High-risk | Approve with controls |
| 3 | Insurance company, support chatbot | Limited risk / transparency | Approve with controls |
| 4 | School district, classroom analytics | Prohibited | Deny, redesign offered |

Two things stand out across all four reviews. First, none of these clients described their own system in AI Act terms, they described a business problem and a tool, which is exactly why the classification work has to start from what the system does to the data and who it affects, not from the client's own label for it. Second, three of the four cases are launchable, but only two of those three are launchable today, the third needs one concrete fix (disclosure) before it can go live, and the fourth needs a real redesign, not a patch.

## Case 1: Predictive maintenance for a production line

**Client need:** An automotive parts manufacturer wants to cut unexpected equipment failures. The proposed AI reads existing sensor data (vibration, temperature, energy use, operating hours) and alerts maintenance staff when a machine looks likely to need servicing.

**Category:** Minimal risk.

**Architecture and role map:** Sensors feed the model continuously, the model flags unusual patterns and sends an alert to the maintenance dashboard. An engineer decides whether to inspect now or wait. If bought from a vendor, the vendor is the provider and the manufacturer is the deployer, if built in house, the manufacturer is both.

**Who is affected:** Mainly the maintenance engineers who receive the alert, and indirectly the production schedule. No customers or job applicants are involved, and no individual worker is being scored or profiled by name.

**Compliance implications:** No AI Act obligations apply, this does not touch people's rights or safety, and it is not critical infrastructure. Worth a quick check that no personal data about individual workers is being profiled, which would be a GDPR question rather than an AI Act one.

**Borderline argument:** Someone could argue that repeated equipment failure predictions tied to a specific shift or operator could turn this into indirect worker monitoring. Worth a one-line confirmation from the client that the model scores machines, not people, before this is fully closed.

**Next artifact:** A one-page internal note describing what data the model uses and who can see its alerts, mainly for the client's own recordkeeping, not a legal requirement.

**Decision:** Approve.

## Case 2: Emergency department triage assistant

**Client need:** A hospital wants to shorten emergency department waiting times using an AI assistant that reads admission data (symptoms, vitals, history, labs, ambulance notes) and recommends how urgently a patient should be seen.

**Category:** High-risk. Annex III names emergency healthcare triage directly as a high-risk use.

**Architecture and role map:** The model outputs a suggested urgency level next to the patient record. Clinical staff must actively confirm or change the priority, this needs to stay a real decision, especially since the hospital's stated goal is for staff to trust the AI more over time, which is exactly the pattern that causes review to quietly become a formality. The vendor building the software is the provider, the hospital is the deployer.

**Who is affected:** Patients arriving at the emergency department, especially anyone whose true urgency does not match what the model predicts from the data available at admission.

**Compliance implications:** The provider owes a risk management system, technical documentation, data governance, accuracy and robustness testing, and registration in the EU high-risk database. The hospital owes a fundamental rights impact assessment before go-live, staff training on when to override the AI, logged override rates, and incident reporting.

**Borderline argument:** The hospital could argue this is "just a recommendation" and therefore lower risk, since a clinician always makes the final call. That argument does not hold up, Annex III classifies the use case itself as high-risk regardless of whether a human sits at the end of it, the human step is a required safeguard, not a reason to downgrade the category. A legal team should still confirm this reading against the final national implementing rules before go-live.

**Next artifact:** A draft fundamental rights impact assessment (FRIA) and a short override logging policy, both needed before the hospital can start using the system, not after.

**Decision:** Approve with controls. Launch is conditional on the provider's documentation being complete and on the hospital having a genuine, logged human review step, not a default click-through.

## Case 3: Insurance customer support chatbot

**Client need:** An insurance company wants an AI chat assistant to answer product, claims, and policy questions, and reduce routine calls to its support team. The assistant does not approve claims or make final decisions.

**Category:** Limited risk / transparency.

**Architecture and role map:** The assistant answers using company documentation and past conversations, and hands the conversation to a human agent when asked or when the issue is complex. If built on a third-party AI platform, that platform is the provider, the insurance company is the deployer using it under its own brand.

**Who is affected:** Customers contacting support with billing, claims, or policy questions, including people who may not realize they are talking to a machine rather than a person.

**Compliance implications:** Article 50 requires that customers are clearly told they are talking to an AI. The brief does not mention this disclosure today, that is the main gap. Chat logs should also be handled under normal GDPR rules since they include personal and policy data.

**Borderline argument:** The company may push back that a chatbot is "obviously" a bot and does not need a disclosure. The brief itself says customers often think they are chatting with a real person, that removes the "it's obvious" exception and makes the disclosure a real requirement, not a nice to have.

**Next artifact:** A short transparency notice, one clear sentence shown at the start of every chat, plus a data handling note for how chat transcripts are stored and used.

**Decision:** Approve with controls, conditional on adding a clear AI disclosure at the start of the chat and a clear marker when it hands off to a human. Without that disclosure, this should not launch.

## Case 4: Classroom engagement analytics platform

**Client need:** A school district wants to understand why participation varies across online classes. The proposed platform analyzes webcam video and microphone audio during live lessons to produce participation and engagement scores, and flags students who may need more attention.

**Category:** Prohibited. Despite being called a "teaching support tool," the system infers attention and engagement from biometric signals (video and audio) about students in an education setting. Article 5(1)(f) bans this, with narrow exceptions for medical or safety reasons that do not apply here. The label the vendor uses does not change what the system does to the data.

**Architecture and role map (as proposed):** Live video and audio feed the model continuously during class, the model infers attention and participation, teachers only see the results afterward with no real-time check on what is being inferred. The vendor is the provider, the school district is the deployer.

**Who is affected:** Students in the virtual classes, a group the AI Act treats as needing extra protection, plus teachers who would end up relying on flags generated from banned inference.

**Compliance implications:** No amount of added controls makes this lawful as designed, this is a banned practice, not a high-risk one that can be managed with safeguards.

**Borderline argument:** The school will likely argue intent matters, the goal is to help students, not to punish or profile them. Good intent does not change the legal analysis, Article 5 bans the method (inferring emotion or attention from biometric data in education), not the motive behind using it. A legal team should confirm this with the vendor's exact technical description before the client fully drops the current design, in case the "interaction patterns" signal turns out to be behavioral logs rather than biometric inference, which would change the classification.

**Next artifact:** A short redesign brief for the vendor, listing exactly which signals are allowed (attendance, on/off time, poll and chat activity) and which are not (any inference from video or audio about a student's internal state).

**Decision:** Deny as proposed.

**Redesign option:** Remove all inference of internal state (attention, emotion, engagement) from video or audio. Replace it with objective, non-biometric activity data only: attendance, camera and mic on-off time, chat and poll participation counts, assignment completion. Teachers keep making the judgment calls about which students need support, the system reports what happened, not what a student was feeling or how attentive they looked.

## Client discussion and final sign-off

I presented this approval pack to Nevena, acting as the client, and she then revealed her private answer key for the four cases.

| Case | My inferred category | Nevena's intended category | Match | Client response |
|---|---|---|---|---|
| 1, predictive maintenance | Minimal risk | Minimal risk | Yes | Accepted |
| 2, hospital triage | High-risk | High-risk | Yes | Accepted |
| 3, insurance chatbot | Limited risk / transparency | Limited risk / transparency | Yes | Accepted |
| 4, classroom analytics | Prohibited | Prohibited | Yes | Accepted |

All four inferred categories matched the intended answer key, and Nevena accepted every decision as presented, including the conditions attached to Case 2 (real human oversight, FRIA, documentation) and Case 3 (AI disclosure), and the redesign path offered for Case 4. No case was challenged or sent back for a different redesign.

**What changed after the client discussion:** Nothing about the classifications or decisions changed, since all four were confirmed correct and accepted as proposed. What the conversation did confirm is that the four briefs carried enough real signal, the data used, who was affected, and whether a human review was genuine, to reach the right call without being told the category upfront. That is a useful check on the briefs themselves, not just on the analysis: a hidden scenario that leads a reviewer to the intended answer through the facts, rather than through an obvious label, is doing its job.

## Debrief

Comparing my inferred classifications against Nevena's intended answer key, all four matched exactly. A few things stood out:

- **Where the hidden scenario worked well:** All four cases. Each brief held onto its legal signal without stating the category outright, for example Case 2 never says "high-risk," but naming emergency triage and admission data was enough to place it under Annex III, and Case 4 called itself a "teaching support tool" while still describing exactly the kind of biometric inference Article 5 bans.
- **Where it was too vague:** None of the four needed a coin flip, each had a specific detail that anchored the classification, the type of data used, who the output affects, and how real the human review step was. That suggests the briefs were pitched at the right difficulty, realistic and not textbook, but not so vague that the category was guesswork.
- **How the recommendation would change after the client conversation:** It would not change on the classification side, since everything was confirmed. The conversation did shift the launch conditions from a proposal into something Nevena has now agreed to act on, meaning the next real step for her is producing the artifacts flagged in each case (the FRIA and logging policy for Case 2, the disclosure notice for Case 3, the redesign brief for Case 4), not re-arguing the category.

## Closing note

Across all four cases, the pattern worth remembering is that the label a client puts on their own tool ("teaching support tool," "maintenance alert," "customer assistant") is not the classification, what the system actually does with the data is. Two cases here (2 and 3) are approvable but only once a specific, concrete condition is met. Case 4 shows that a well-meaning goal, helping teachers support students, does not excuse a banned method of getting there. The client discussion confirmed all four calls were right, which is the outcome this exercise is meant to test, whether the classification holds up once the real answer is on the table, not just on paper.
