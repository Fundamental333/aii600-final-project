# Decisions

This file is the history of the project. Append an entry when a choice changes the work: the quantity, the data, the split, the model, the loss, or the action. Leave old entries in place. A later entry can reverse an earlier one. If a result depends on a random draw, record the seed under Why. The split entry records the cutoff date, or the seed and the fraction. The pull request that merges the code names this entry.

## 2026-10-30: Choose the EEG Drift Monitor project

- Decision. Build an EEG Drift Monitor that estimates changes in relative alpha power between recording visits and recommends keeping the baseline, replacing it, or collecting more EEG.

- Why. This connects probability, Bayesian estimation, uncertainty, and decision costs to a practical task. OpenNeuro ds007176 provides repeated recordings. A two-person development pilot successfully processed real EEG, but also showed that a short probe can give a misleading estimate. These participants will be excluded from final testing. The planned random seed for participant splitting and resampling is 600; exact split details will be recorded when implemented.

- Alternative. Building a complete EEG authentication system was set aside because enrollment, impostor testing, and security evaluation would substantially expand the project. Authentication remains a possible future application.

- Revisit. Revise the model, probe duration, or update rule if testing on new participants shows unreliable estimates, inaccurate uncertainty intervals, or no benefit over simpler rules. The initial drift threshold and penalty values are assumptions to test.

- AI assistance. ChatGPT helped in polishing the text and proposal for Github.
