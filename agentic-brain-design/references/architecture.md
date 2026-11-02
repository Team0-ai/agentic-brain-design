# Questions for designing a brain

Use these questions to choose what a system needs. They describe problems to resolve, not a fixed architecture to copy. Start with the user's sources, tasks and access needs. For each capability, explain why they need it now, can defer it, or do not need it.

## 1. Sources

Which sources contain the information the agents need? Who permits access, how will changes arrive, and how will you know a source stopped updating? If meetings are included, how will participants know they are being recorded?

## 2. Ingest

What happens when an input arrives twice, arrives late, or fails halfway through processing? Can a large import delay new information? How will the system distinguish questions and reports of actions from evidence that something happened?

## 3. Write rules

Who can confirm each kind of fact, and what evidence is needed? How will you distinguish people from automated senders, resolve identities, and handle uncertain matches? Will every source and worker follow the same rules? How will secrets be kept out?

## 4. Stored information

Which people, organizations and work things need records? Which statements need links between them? What history and source evidence must remain available so a reader can check an answer?

## 5. Facts and evidence

How will you distinguish when something happened, when it was said, and when it was stored? How will uncertainty and corrections be represented? Can someone trace a fact back to what supports it?

## 6. Changes and disagreements

What evidence allows a new value to replace an old one? When should both remain visible? Who can resolve a disagreement, and how will the answer reach the system? How will a correction affect information derived from the old value? If promises matter, what proves one was kept?

## 7. Upkeep

What must happen immediately, and what can wait? How quickly does the information change? What needs another look when more evidence arrives? When a rule improves, which retained information needs reprocessing? How will you detect failed upkeep and verify recovery?

## 8. Private and shared information

Who may read, share, correct and withdraw information? How will consent, attribution and access rules be enforced? What happens to copies and derived information after withdrawal? What can administrators and server operators access? Which information belongs to a person, and which belongs to the company?

## 9. Reads

What does the agent need for the task at hand? How will the system resolve names, find relevant information and preserve its current or uncertain state? How will it distinguish no matching information from a failed search? How will every read enforce access rules?

## 10. Agent access

How does each agent authenticate, and which reads and writes may it perform? How can someone revoke access? What activity must be recorded to investigate a mistake? If agents communicate with each other, whose permission is required?

## 11. Agent behavior

When should an agent read, and what should it save? Which hosts support instructions, tools or hooks? How will you check that these actually ran, and what should happen when context is unavailable? How will users know an answer relied on stored information?

## 12. Human control

Where do people already work, and how will unresolved questions reach them there? How can they correct a fact, pause a source, restrict learning or inspect access? How will corrections remain effective when old information is imported again?

## 13. Retention

What must be kept to support useful answers, history and reprocessing? What should be deleted to protect people? Define policies separately for raw inputs, learned facts and access records. What happens when someone leaves? How will deletion affect copies, indexes and backups, including after a restore?

Use the scoring method and worked examples in the walkthroughs to check the choices against real tasks. Include changing facts, access boundaries and the effort needed to keep the system working.
