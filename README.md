# The Effect of Norepinephrine on Dendrites of Cortical Neurons

### Dr. Michael London Laboratory of neural coding at ELSC - The Hebrew University of Jerusalem

**Abstract**

Neuromodulation is an important neuronal process by which one or more chemicals regulate the activity of various populations of neurons. One particular neuromodulator is norepinephrine (NE). NE has been demonstrated to have an important role in modulating attention (Berridge and Waterhouse., 2003), arousal (Carter et al., 2010) and working memory (Wang et al., 2007). In the brain, NE release occurs mainly through the activation of a region in the brainstem called the Locus Coeruleus (LC). This small nucleus is the origin of most NE pathways in the brain. Nowadays, guanfacine which is an agonist of NE-receptors, is being used as a component in medication for treating ADHD and has been shown to be effective. Currently, there is no satisfying explanation as to why guanfacine effects ADHD symptoms, and much is yet to be studied about its operation in the brain. Our hypothesis is that NE modulates the activity in dendrites of pyramidal neurons in the cortex, and my proposed research will test some aspects of this hypothesis.

The full work :

![Final_project](Final_project.pdf)

---

## The ROIProcessor pipeline input :

---

**workingDirectoryBefore** - the before time frame tiff images path
usually used to analyze before the exposure time frame, but can also use any other time frame

**workingDirectoryAfter** -  the after time frame tiff images path
usually used to analyze after the exposure time frame (10-60 minutes), but can also use any other time frame

**compFlag** - true runs a comparison between the two time frames, false only analyze one time frame (should have the same path to before and after directories)

**dispEdgeDec** - if true displays some images from the edge detection stage
Edge detection images - indicates the marked ROIs (when comparing two time frames -  montage of edge detection) Filled edge detection images - indicates the pixels the pipeline will extract information from

**dispTranslation** - if false displays some images from the translation stage(relevant only for when comparing) Always displaying (in compersion mode) the cross correlation outcome - before according to after and after accoriding to before the white is overlapping points
optional - to see filled ROI images with shared ROIs, excluded ROIs(out of one time frame coordinates), exclusive ROIs (only in one of the time frames)

**runNum** - the run number, used as folder name for the output files (needs to be different if you run in parallel)

---

### The two run options :

---

1. **Single time frame** (all scripts names end with S - single)

Run as - ROIProcessor(path, path, false, true/false, false, runNum as a string - '1' )

output files -
totalROIMeanNormelized -  contain normelized pixels mean per ROI for each image in the time frame (7200 frames -> 7200 means)

2. **Comparing two different time frames** (all scripts names end with C - comparison)

Run as - ROIProcessor(path1, path2, true, true/false, true/false, runNum as a string - '1' )

output files -
All the output files contain normalized pixels mean per ROI for each image in the time frame (7200 frames -> 7200 means)

sharedMeanAfterPerFrameNormelized/ sharedMeanBeforePerFrameNormelized - common ROIs

existOnlyBeforeMeanPerFrameNormelized - ROIs which exist only before
addedToAfterFromBeforeMeanPerFrameNormelized - ROIs which appear only in the before time frame and were added to the after time frame (so we can compare)

existOnlyAfterMeanPerFrameNormelized - ROIs which exist only after
addedToBeforeFromAfterMeanPerFrameNormelized - ROIs which appear only in the after time frame and were added to the before time frame (so we can compare)