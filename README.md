# handwritten_txt_recognition
This is a **handwritten text recognition (HTR) pipeline** that operates on **scanned pages** and applies the following
operations:

* Detect words
* Read words

* Go to `scripts/`
* Run `python demo.py`
Configuration is done by passing instances of these dataclasses to the `read_page` function:
* `DetectorConfig`: configure the word detector
* `LineClusteringConfig`: configure the line clustering algorithm
* `ReaderConfig`: configure the text reader

The most important parameter for the detector is the scale.
The detector works best for text of height 50px. 
Setting a scale != 1 automatically resizes the image before applying te detector.
Example: Text height h is 100px in the original image. Set the scale to 0.5 so that detection happens at the ideal text size.

The second most important parameter for the detector is the margin. 
It allows adding a few pixels (blue) around the detected words (red) which might improve reading quality.

For the line clustering algorithm the minimum number of words can be set with the parameter `min_words_per_line`.
Lines which contain fewer words will be ignored.
Example: it is known that all lines contain 2 or more words. Then set the parameter to 2 to ignore false positive detections that form lines with only a single word.
