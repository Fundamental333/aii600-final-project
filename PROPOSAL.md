# Proposal



## Hypothesis

Combining an earlier EEG baseline with a short new recording can reduce the cost of baseline-update decisions compared with always updating or never updating.


I will build an EEG Drift Monitor to help decide when a person’s stored EEG reference needs to be updated. When the person returns for another recording, their EEG may differ from that baseline. The tool will measure this EEG drift and recommend keeping the baseline, replacing it, or collecting more data before deciding.

To measure drift, I will track relative alpha power: the percentage of EEG power within the selected 4–30 Hz range that comes from alpha waves, which occur at 8–13 Hz.  I will test short recordings of 20, 40, and 60 seconds - this is called probes. Each probe will be used to estimate the change. A separate 60-second recording segment, kept out of that estimation, will check how accurate the estimate was.

I will compare three methods: assuming the baseline has not changed, estimating the change from the probe alone, and using a Bayesian probability model to combine information from the baseline and probe. The Bayesian model will also estimate uncertainty, showing how confident we should be in its result.





## Data



I will use [OpenNeuro ds007176](https://openneuro.org/datasets/ds007176), collected by Henao Isaza et al. It contains repeated EEG recordings across approximately two years, including eyes-closed recordings from 39 people with multiple visits before quality checks. Each case will compare an earlier and later visit for one person.

An initial two-person trial already loads real EEG and produces estimates and plots. These people will be excluded from final testing. Different people will be used to develop, adjust, and test the model. The short sample and checking segment will stay separate. The CC0 license allows resharing; analysis data and file checksums will be provided through a GitHub release called `data`.

## Decision affected by the model


An EEG-system operator decides whether to record a new reference. Initially, replacing it costs 1 penalty point; keeping it when the alpha-power change exceeds 5 percentage points costs 5 points. Extra recording time also carries a penalty. These are assumptions, and I will test other values.

Testing will compare wrong decisions, estimation errors, uncertainty, and recording time on unused data. Changing alpha power alone does not establish authentication failure. Authentication remains a possible future application.
