# A Protocol for Comparing Audio and Audiovisual Guidance Modalities in Coherent Breathing Using Consumer-Grade EEG

## Abstract

Coherent breathing at 0.1 Hz (6 s inhalation / 6 s exhalation) is a widely used self-regulation technique, yet the guidance modality through which the breathing rhythm is delivered—auditory pacing alone versus synchronized auditory and visual pacing—is typically chosen on design grounds rather than measured empirically. This protocol specifies a complete, reproducible procedure for comparing the two modalities within a single session using a 14-channel consumer-grade EEG system (Emotiv Epoc X) and the Performance Metrics available in Emotiv Studio.

The protocol covers creation of matched pacing stimuli (an auditory asset authored in Logic Pro and a visually synchronized animation authored in TouchDesigner, both driving an identical 6 s/6 s cycle), sensor preparation and signal-quality verification, a fixed session structure of a 240-second eyes-open resting baseline followed by two 5-minute guided breathing blocks, and export of three classes of quantitative output: baseline-corrected Performance Metrics (Stress, Attention, Engagement, Excitement, Interest), relative band power across theta, alpha, low beta, high beta and gamma, and frontal alpha asymmetry. A structured post-session qualitative capture is included, since subjective ease of following the pacing is a primary outcome that EEG does not index directly.

The procedure requires approximately 25 minutes of participant time per session and uses equipment and software available outside a dedicated laboratory. It is applicable to single-subject repeated-measures designs and scales to group designs without modification. Condition order must be randomized or counterbalanced; guidance for doing so is given explicitly, as is a full account of the critical steps—signal quality, eyes-open consistency across all phases, and breathing-pacing accuracy—on which the validity of the comparison depends.

## 1\. Introduction

### 1.1 Coherent breathing and resonance frequency

Coherent breathing (also termed resonance-frequency or paced breathing) prescribes slow, evenly divided respiration at approximately six breaths per minute. At this rate (0.1 Hz) respiratory and baroreflex oscillations align, producing the characteristic large-amplitude heart-rate oscillation used as a target in HRV biofeedback. The pattern applied here, 6 s inhalation and 6 s exhalation with no hold, yields exactly ten breaths per minute and is the most commonly used implementation.

Because the respiratory target is fixed and easily specified, coherent breathing is a useful test bed for isolating variables *other* than the breathing pattern itself. This protocol isolates one such variable: the sensory channel through which the pacing instruction is delivered.

### 1.2 Guidance modality as an experimental variable

Practical implementations of paced breathing differ substantially in how the rhythm is conveyed. Auditory implementations use tones, swells, or spoken counts; visual implementations use expanding and contracting shapes, moving bars, or progress arcs; many combine both. These choices are rarely evaluated against one another, yet the guidance channel plausibly affects how accurately a participant tracks the target rhythm, how much attentional effort tracking requires, and how the session is experienced affectively. If modality alters any of these, it is a component of the intervention rather than a presentational detail.

This protocol therefore compares two conditions that hold the respiratory target constant and vary only the guidance channel:

- **Audio**: auditory pacing cues only.  
- **Audio & Video**: the same auditory pacing cues accompanied by a temporally synchronized visual animation.

### 1.3 Consumer-grade EEG as an accessible research tool

Research-grade EEG systems constrain this kind of question to laboratory settings. Consumer-grade systems such as the Emotiv Epoc X provide 14 channels at fixed 10-20 locations with saline-based sensors, at a cost and setup time that permit repeated single-subject designs and field data collection. Their limitations are real and are addressed in Section 7: fixed and sparse spatial sampling, greater susceptibility to motion and electromyographic artifact, and reliance on vendor-computed composite metrics whose underlying algorithms are proprietary.

The design consequence is that this protocol is specified as a *within-session, within-subject* comparison. Both conditions are recorded from the same montage in the same sitting and each is expressed as a change from that session's own baseline, so the comparison does not depend on absolute calibration of the vendor metrics, only on their sensitivity to a difference between two conditions recorded minutes apart.

---

## 2\. Materials

### 2.1 Hardware

| Item | Specification | Notes |
| :---- | :---- | :---- |
| EEG headset | Emotiv EPOC X, 14 channels | Channels AF3, F7, F3, FC5, T7, P7, O1, O2, P8, T8, FC6, F4, F8, AF4; references at P3/P4 locations |
| Sensors | Saline (wet) felt pads | Hydrate immediately before fitting; keep spare pads |
| Saline solution | Contact-lens multipurpose or sterile saline | Sufficient for full re-wetting mid-session if required |
| Recording computer | Desktop or laptop meeting Emotiv Studio requirements | Bluetooth LE or USB receiver for headset link |
| Audio playback | Over-ear headphones or near-field monitors | Use the same playback path in both conditions |
| Visual display | Monitor at fixed viewing distance | Position and brightness held constant across sessions |
| Seating | Upright chair with back support, no armrest slouch | Fixed position relative to display |

### 2.2 Software

| Item | Purpose |
| :---- | :---- |
| Emotiv Studio | Experiment configuration, recording, Performance Metrics computation, data export |
| Logic Pro | Authoring the auditory pacing asset |
| TouchDesigner | Authoring the synchronized visual pacing asset |

### 2.3 Room setup

Record in a quiet room with stable, indirect lighting and no direct sunlight on the display. Silence phone and computer notifications. Keep ambient temperature comfortable and constant, since thermal discomfort introduces movement artifact. Position the chair so the display is at eye level at a fixed distance, and mark the chair position so it can be reproduced in later sessions.

### 2.4 Participant screening

Screen and record: absence of diagnosed neurological conditions; absence of current psychiatric medication; no caffeine within two hours of the session; no alcohol within 12 hours. Where the protocol is used with participants other than the experimenter, obtain ethics approval and informed consent appropriate to the institution before any recording.

## 3\. Stimulus preparation

Prepare both assets before the first recording session and reuse the identical files across all sessions. The two assets must be temporally identical — the same cycle length, the same phase boundaries, the same total duration.

### 3.1 Auditory pacing asset (Logic Pro)

1. Create a project at a tempo that divides evenly into the 12-second respiratory cycle. At 120 BPM, one cycle is 24 beats; at 100 BPM, one cycle is 20 beats.  
2. Build one 12-second cycle: a 6-second inhalation segment and a 6-second exhalation segment, each cue distinguishable from the other so the participant can identify the current phase without counting.  
3. Verify segment boundaries against the project timeline to sample accuracy. Phase boundaries must land at exact 6.000-second intervals; drift accumulates audibly over a 5-minute block.  
4. Loop the cycle to a total duration of 300 seconds (25 complete cycles).  
5. Apply a short fade-in at the start and fade-out at the end of the 300-second block to avoid transient onset artifact in the EEG.  
6. Normalize to a fixed peak level, record that level, and reuse it for every session.  
7. Export as uncompressed audio (WAV, 44.1 kHz or higher).

### 3.2 Visual pacing asset (TouchDesigner)

1. Build an animation whose visual state maps monotonically onto respiratory phase. For example, a form that expands continuously across the 6-second inhalation and contracts continuously across the 6-second exhalation, so that instantaneous position within the phase is readable at a glance.  
2. Drive the animation from a timing source locked to the same 12-second cycle as the audio asset. Derive both from a single canonical cycle definition rather than setting each independently.  
3. Confirm synchronization empirically: play the audio and visual assets together and verify that phase transitions coincide at the start, middle, and end of the 300-second duration. Correct any accumulated offset before use.  
4. Keep luminance broadly constant across the cycle. Large brightness swings synchronized to the respiratory cycle will appear in the occipital EEG as a visually evoked response confounded with the breathing phase.  
5. Render to a fixed-duration 300-second video file at the display's native resolution and refresh rate, rather than running the network live, so that every session receives a bit-identical stimulus.

### 3.3 Condition definition

- **Audio & Video** condition: the 300-second video asset with the 300-second audio asset, played together.  
- **Audio** condition: the 300-second audio asset alone, with the display showing a static neutral field at the same mean luminance as the video asset. Do not turn the display off or leave a bright desktop visible — the visual environment should differ between conditions only in the presence of pacing information, not in overall light level.

## 4\. Protocol

### 4.1 Sensor preparation and signal-quality check

1. Hydrate all 16 felt sensor pads (14 channels plus two references) in saline until saturated but not dripping. Insert into the sensor housings.  
2. Seat the headset with the reference sensors on the mastoid or P3/P4 locations per the manufacturer's fitting guide, and confirm the frontal arm sits symmetrically. Check symmetry visually against a mirror or a second observer—asymmetric placement is a direct threat to any asymmetry measure computed later.  
3. Open Emotiv Studio and display the contact-quality and EEG-quality maps.  
4. Adjust sensors individually until all 14 channels report good contact quality. Where a channel remains poor, re-wet that pad, part hair beneath it, and reseat; do not proceed with a channel excluded unless the study design accounts for it.  
5. Confirm EEG quality (signal-quality index) in addition to contact quality. Contact quality alone can read acceptable on a channel that is still noisy.  
6. Record a 30-second quiet check recording. Inspect for line noise, electromyographic contamination from jaw or neck tension, and eye-blink artifact of expected morphology. Resolve before continuing.  
7. Log the achieved contact and EEG quality per channel in the session record. Report this per session in any write-up.

### 4.2 Session configuration in Emotiv Studio

8. Create an experiment definition containing three labelled recording markers: `baseline`, `block_1`, and `block_2`.  
9. Enable Performance Metrics computation (Stress, Attention, Engagement, Excitement, Interest) and confirm that band-power output is being retained.  
10. Set the baseline period used for Performance Metrics correction to the 240-second `baseline` segment, so that both guided blocks are expressed relative to the same resting reference within that session.  
11. Verify the recording is capturing before starting the baseline. A failed recording discovered after the fact costs the whole session, since the two conditions must be compared within a session.

### 4.3 Condition order assignment

12. **Randomize or counterbalance condition order across sessions and across participants.** Assign the order for the upcoming session before the participant is seated, from a pre-generated randomization list or a counterbalanced sequence (for a repeated single-subject design, alternate ABBA / BAAB across sessions).  
13. Record the assigned order in the session log before recording begins.

>   
> **Note on the original run.** The single-subject demonstration that motivated this protocol used a fixed order in every session—Audio & Video first, Audio second. This is a known limitation of that specific run, not of the protocol: order effects and modality effects cannot be separated under a fixed order. Any use of this protocol should follow step 12\.

### 4.4 Session sequence

14. Seat the participant upright in the marked chair position, feet flat, hands resting on the thighs, at the fixed viewing distance from the display.  
15. Instruct the participant to **keep their eyes open throughout the entire session**—baseline and both guided blocks alike—blinking normally, gaze directed at the display. Eyes-open state must be identical across all phases so that occipital alpha differences between conditions are not driven by eyelid state.  
16. Instruct the participant to minimize head, jaw, and limb movement, to avoid clenching the jaw, and to swallow rather than suppress the urge to swallow.  
17. **Baseline (240 s).** Start the `baseline` marker. The participant sits quietly, eyes open, breathing naturally with no pacing stimulus and no task. Do not converse during the baseline.  
18. Allow a brief, fixed inter-block interval (30–60 s, identical every session) between segments. Do not extend it for one condition and not the other.  
19. **Guided block 1 (300 s).** Start the `block_1` marker and launch the asset for the condition assigned to position 1\. The participant breathes with the pacing cue: **6 s inhalation, 6 s exhalation, no hold, nasal inhalation, seated upright, eyes open.** Instruct them to follow the pacing as accurately as they can and to use full but unstrained lung capacity.  
20. At the end of the 300 seconds, stop the marker. Allow the same fixed inter-block interval as in step 18\.  
21. **Guided block 2 (300 s).** Start the `block_2` marker and launch the asset for the condition assigned to position 2\. Same breathing instruction as step 19\.  
22. Stop the recording. Verify that all three segments are present in the file, with the expected durations, before removing the headset.  
23. Remove the headset, rinse the felt pads in clean water, and leave them to dry.

### 4.5 Data export

24. Export **Performance Metrics** for each segment, baseline-corrected against the 240-second `baseline` segment: Stress, Attention, Engagement, Excitement, Interest. Retain the per-condition values with the condition label and session number.  
25. Export **band power** for both guided blocks across theta, alpha, low beta, high beta, and gamma. Record whether values are absolute or relative, since the two are not interchangeable in later comparison.  
26. Export **frontal alpha asymmetry**, and record alongside it the **electrode pair and sign convention** used by the software version in use. Do not assume the convention: FAA is reported in the literature in both directions and with several electrode pairs, and directional interpretation is meaningless without it. If the convention cannot be confirmed from documentation, report the values without directional interpretation and state that the convention is unconfirmed.  
27. Export the **topographic maps** for both guided blocks with an identical colour scale across conditions. Maps rendered on independently auto-scaled ranges cannot be compared visually.  
28. Export or screenshot any **aggregated report** the software generates across sessions, and record the software version and build number in the session log.  
29. Archive all exports with a session identifier, date, condition order, and the per-channel signal-quality log from step 7\.

### 4.6 Post-session qualitative capture

Collect these notes immediately after each session, before reviewing any EEG output, and record them verbatim. Subjective ease of pacing is a primary outcome that the Performance Metrics do not index.

30. Administer the following prompts, one per condition, in the order the conditions were presented:  
    - **Ease of following pacing**: How easy was it to follow the breathing rhythm? Where in the cycle, if anywhere, did you lose it?  
    - **Lung capacity use**: Did the pacing let you use your lung capacity comfortably, or did you feel rushed, or short, at either end of the cycle?  
    - **Phase transitions**: Did you know when the switch from inhalation to exhalation was coming, or did it arrive unexpectedly?  
    - **Distraction and mind-wandering**: How often did attention leave the breathing? What pulled it away?  
    - **Physical sensations**: Any lightheadedness, air hunger, tension, or discomfort? Where?  
    - **Overall preference**: Which condition would you choose to do again, and why?  
31. Record the response as written, without editorial smoothing. Note any spontaneous observation that falls outside the prompts, and flag whether it was volunteered before or after the participant saw any data.  
32. Where the experimenter is also the participant, write the notes before opening any exported file, and note in the log that the design is unblinded.

## 5\. Representative results

This protocol produces four classes of output per session.

**Baseline-corrected Performance Metrics** yield one signed value per metric per condition, expressing change from the resting baseline. Across conditions these are compared as differences in the direction and magnitude of change. For example, one condition showing a reduction in Stress while the other shows little change or a slight increase. With three or more sessions, per-session values allow the consistency of the direction of change to be inspected across repeats.

**Relative band power comparisons** yield a five-band profile per condition, supporting statements about which condition showed broadly higher power and in which bands the difference was largest. Because the bands are not independent, the informative output is the pattern across bands rather than any single band in isolation.

**Frontal alpha asymmetry** yields one value per condition. Interpreting its direction requires the electrode pair and sign convention (step 26); without those, the values are reportable but not interpretable.

**Qualitative notes** yield the participant's account of pacing accuracy, attentional stability, and preference which, in a modality comparison, frequently carries information the composite metrics miss entirely.

### 5.1 Illustrative single-subject demonstration

The following is offered only to show the *form* of the output. It comes from a single-subject (N \= 1\) run of this protocol across three sessions with a **fixed** condition order (Audio & Video first in every session), analyzed solely by the vendor software's own aggregated report. These are not validated findings, they are not independently analyzed, and they should not be treated as an expected result.

In that run, the aggregated report described a substantial reduction in Stress under Audio & Video (−26.99 baseline-corrected) against a slight increase under Audio (+0.52); higher Engagement under Audio & Video (+12.85) than Audio (+4.78); a larger decrease in Excitement under Audio & Video (−19.39) than Audio (−5.58); a larger decrease in Interest under Audio & Video (−14.85) than Audio (−1.77); and comparable Attention across conditions (Audio 1.80, Audio & Video 2.25). Band power was higher in the Audio condition across all five bands, with the largest gap in theta and the next largest in alpha, and the topographic maps showed more widespread activity in the Audio condition. Frontal alpha asymmetry was 0.026 for Audio & Video and 0.141 for Audio, reported without directional interpretation because the electrode pair and sign convention were not confirmed.

The pattern—one condition more affectively settled while the other showed higher band power—illustrates a case where the vendor composites and the spectral output point in different directions, and where the qualitative notes are needed to make sense of the discrepancy. It is exactly the situation this protocol is designed to surface rather than resolve.

## 6\. Critical steps

Failure at any of the following compromises the comparison, and each is worth verifying explicitly rather than assuming.

**Signal quality (steps 1–7).** Consumer saline sensors dry over a 25-minute session. Verify quality before the baseline and inspect the record afterwards for progressive degradation across the session; a quality drift that tracks the session timeline will masquerade as a condition effect, since the conditions are separated in time.

**Headset placement symmetry (step 2).** Any asymmetry measure is only as good as the physical symmetry of the montage. Fit symmetrically, and refit rather than accept a visibly offset frontal arm.

**Eyes-open consistency (step 15).** Occipital alpha is strongly modulated by eyelid state. If eyes are open in one phase and closed or partly closed in another, the band-power comparison is confounded at its most sensitive point. Keeping eyes open in *every* phase, including baseline, is what makes the baseline correction meaningful.

**Matched visual environment (Section 3.3).** The Audio condition must present a static field at matched mean luminance rather than a dark or absent display, so the conditions differ in pacing information and not in light level.

**Breathing pacing accuracy (step 19).** The manipulation is the guidance channel, not the breathing rate. If the participant tracks 6 s/6 s well in one condition and drifts in another, respiratory rate itself becomes a confound, which is why step 30 asks directly about where the rhythm was lost, and why that answer is part of the result rather than a footnote to it.

**Stimulus synchronization (step 3.2.3).** Audio and visual phase boundaries must coincide throughout the full 300 seconds. Small per-cycle offsets accumulate into a visible mismatch by the end of a block.

**Order assignment before seating (steps 12–13).** Assign and log the order before the session starts. Deciding at the console, or letting the order follow habit, reintroduces the confound the step exists to remove.

## 7\. Discussion

### 7.1 Strengths

The equipment is accessible: a consumer EEG headset, a DAW, and a visual-programming environment, none requiring a dedicated laboratory. Sessions are short—roughly 25 minutes of participant time including setup—which makes repeated measures within a single participant practical and reduces attrition in group designs.

The stimulus creation pipeline is fully specified and reproducible. Because both assets derive from a single canonical 12-second cycle definition and are rendered to fixed-duration files, the stimulus another investigator builds from Section 3 is functionally the same stimulus, and the two conditions differ in exactly one respect by construction.

The within-session design is the protocol's main methodological strength. Both conditions are recorded from one montage in one sitting, each referenced to the same baseline, which removes between-session variance in sensor placement, hydration, time of day, and participant state from the comparison of interest.

### 7.2 Limitations of consumer-grade EEG

Spatial sampling is sparse and fixed: 14 channels at predetermined locations, without the density for source localization or the flexibility to add coverage where a hypothesis requires it. Saline sensors give higher and less stable impedances than gel-based research systems and degrade over a session. Frontal channels sit close to the eyes and to facial musculature, so ocular and electromyographic artifact is a persistent concern in precisely the region relevant to frontal asymmetry.

The most consequential limitation is the vendor-computed metrics. Performance Metrics such as Stress, Attention, Engagement, Excitement, and Interest are proprietary composites; their underlying features, weightings, and validation are not fully published, they may change between software versions, and their construct labels should not be read as validated psychological measurements. Treat them as reproducible device outputs that are sensitive to state change—useful for within-session comparison, weak ground for cross-study claims. Recording the software version (step 28\) is what allows a later reader to know which version's algorithm produced a given number.

Frontal alpha asymmetry deserves separate mention. Its interpretation depends entirely on the electrode pair and the sign convention, both of which vary across the literature and are not always documented in consumer software. Reporting an FAA value without its convention is not interpretable, and inferring a direction from an unconfirmed convention is worse than reporting no direction at all.

### 7.3 Design considerations for future use

**Counterbalancing is not optional.** A fixed condition order confounds modality with time-on-task, sensor drift, and cumulative relaxation across the session—all of which run in the same direction as a plausible modality effect. Step 12 exists to remove this, and a run that skips it can describe a difference between blocks but cannot attribute it to modality.

**Blinding is limited by the manipulation.** A participant necessarily knows whether a screen is showing pacing information, so condition blinding is impossible. What can be controlled is the experimenter's influence on data handling, and in single-subject work (where experimenter and participant are the same person) recording qualitative notes before opening any exported file (step 32\) is the available safeguard.

**Sample size and inference.** In a single-subject design, per-session values across repeats describe the consistency of a direction of change; they do not license population inference, and the number of repeats needed for even a descriptive claim about consistency is more than a handful. Group application of this protocol requires no procedural change beyond the randomization in step 12 and an analysis plan specified in advance.

**Natural extensions.** The protocol accommodates additional guidance conditions without structural modification. For instance, an auditory condition carrying explicit phase-transition information (a pitch contour in the final seconds of each phase) to test whether an audiovisual advantage, where observed, reflects the availability of temporal-prediction information rather than the visual channel per se. Concurrent photoplethysmography or ECG would allow the respiratory-pacing manipulation to be verified physiologically rather than by self-report, which addresses the pacing-accuracy confound noted in Section 6 directly.

## 8\. Author contributions

The author conceived the study, designed the protocol, created the audio and visual stimuli, collected the data as the sole participant, interpreted the results, and wrote the manuscript. (Contributor roles follow the CRediT taxonomy: conceptualization; methodology; software and stimulus development (audio and visual); investigation; formal analysis; writing, original draft; writing, review and editing.)

## 9\. Conflicts of interest

The author is employed by Emotiv, the manufacturer of the Epoc X headset and the Emotiv Studio software used in this study, including the Performance Metrics reported here. The Performance Metrics are proprietary Emotiv algorithms. \[Include only the statements that are true:\] \- \[The equipment used was purchased personally / provided by Emotiv.\] \- \[This work was done independently of the author's employment, on the author's own time, and was not funded or directed by Emotiv.\] \- \[Emotiv did / did not review this document before publication.\] \- \[The author did / did not contribute to developing the Performance Metric algorithms.\] \- \[The views expressed are the author's own and do not represent Emotiv.\] \[The author has no financial interest in breathwork or meditation products, apps, or services.\] This protocol was not funded by any external source.

## 10\. Ethics statement

This was a self-experiment. The sole participant was the author, who designed the protocol, understood its procedures and risks, and consented to participate. The procedures are non-invasive (consumer EEG and paced breathing). The author reports no neurological conditions and no current psychiatric medication. No ethics committee review was sought because no participants other than the experimenter were involved. Anyone applying this protocol to other participants must obtain approval from an appropriate ethics body and informed consent from each participant, and should screen for conditions where paced breathing or EEG recording may be unsuitable.