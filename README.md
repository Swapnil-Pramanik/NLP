# NLP

Coursework repository for **CSET346 — Natural Language Processing (Lab)**,
B.Tech. Specialization / NSPL Elective-I. Each week's lab assignment lives in
its own folder as a self-contained Jupyter notebook plus the original
assignment PDF.

## Structure

```
NLP/
├── README.md              # this file
├── requirements.txt        # pinned Python dependencies (pip freeze from venv/)
├── .gitignore
├── venv/                   # local virtualenv (not tracked)
└── week1/
    ├── 2026_ODD_Week_1_Assignment_Intro.pdf   # original assignment brief
    ├── week1.ipynb                            # completed lab notebook
    └── data/                                  # generated sample files (not tracked)
```

## Week 1 — Environment & Text Data Handling

`week1/week1.ipynb` implements Lab-01 sequentially, one cell per sub-task:

**Task 1 — Getting familiar with the environment.** For each data-format
family called out in the assignment (tabular/interchange: `.dat` `.csv`
`.tsv` `.arff`; spreadsheet: `.xlsx` `.ods`; `.json` `.ubj` `.html` `.xml`;
binary: `.pkl` `.h5` `.zip` `.sql` `.mat` `.npy` `.npz`; images: `.jpg` `.png`
`.bmp` `.tiff` `.dcm` `.mha`; video: `.mp4` `.avi` `.mpeg`; audio: `.wav`
`.mp3` `.midi`; text: `.txt` `.pdf` `.docx`) the notebook loads a genuine,
widely-used public dataset, re-saves it into the target format, reads it
back with the appropriate library, prints its properties (shape/size/dims/
etc.), and visualizes it (line/bar/histogram/pie/scatter, image plots, a
video player, an audio player + spectrogram, and a word cloud / bubble
chart). The datasets used: **Iris** (tabular/`.arff`), **Wine**
(spreadsheet/`.xml`), **Titanic** via `seaborn` (`.json`/`.ubj`/`.html`/
`.sql`), **Digits** (`.h5`/`.npy`/`.npz`), SciPy's **raccoon face** demo
image (`.mat`), scikit-image's **astronaut** test image (`.jpg`/`.png`/
`.bmp`/`.tiff`), a real anonymized CT slice bundled with `pydicom`
(`.dcm`), scikit-image's **cells3d** fluorescence-microscopy volume
(`.mha`), OpenCV's canonical **`vtest.avi`** pedestrian sample video
(`.mp4`/`.avi`/`.mpeg`), librosa's **trumpet** demo recording (`.wav`/
`.mp3`), a real **J.S. Bach chorale** (BWV 66.6) from `music21`'s corpus
(`.midi`), and Lewis Carroll's **Alice's Adventures in Wonderland** from
NLTK's Gutenberg corpus (`.txt`/`.pdf`/`.docx`/word cloud). Two very
legacy formats (`.sxc`, `.dif`, legacy binary `.xls`) have no maintained
read/write library on Python 3.13 and are called out as unsupported rather
than faked.

**Task 2 — Text data cleaning & normalization.** Implements the 7-step
cleaning pipeline (lowercasing, whitespace, contractions, special
characters, repeated letters, punctuation, URL artifacts) over `re` on the
5 uncleaned paragraphs from the assignment, then runs the 5 NLTK
experiments: tokenizing the Brown corpus, visualizing raw word frequencies
(bar chart + word cloud), Porter stemming, WordNet lemmatization, and a
stemming-vs-lemmatization frequency comparison.

## Setup

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python -m ipykernel install --user --name=nlp-week1 --display-name "Python (NLP week1)"
```

Also requires `ffmpeg` on `PATH` for MP3 encoding (`brew install ffmpeg`),
an internet connection on first run (to download Titanic via `seaborn`,
`vtest.avi` from the OpenCV GitHub repo, the librosa trumpet clip, and the
scikit-image/scipy demo datasets — all cached locally afterwards), and NLTK
corpora downloaded on first run via `nltk.download(...)` (brown, gutenberg,
punkt, punkt_tab, stopwords, wordnet, omw-1.4, averaged_perceptron_tagger).

Run the notebook with the `nlp-week1` kernel in Jupyter/Colab/VS Code.

## Dependencies

Key libraries: `pandas`, `numpy`, `matplotlib`, `scipy`, `h5py`, `openpyxl`,
`odfpy`, `lxml`, `pillow`, `opencv-python-headless`, `pydicom`,
`SimpleITK`, `soundfile`, `pydub`, `pretty_midi`, `wordcloud`, `nltk`,
`liac-arff`, `py-ubjson`, `python-docx`, `pypdf`, `reportlab`,
`scikit-learn`, `scikit-image`, `seaborn`, `librosa`, `music21`. Full
pinned list in `requirements.txt`.
