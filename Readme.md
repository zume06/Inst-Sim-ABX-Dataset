# Instrumental Similarity ABX Dataset
This is the similarity annotation for the instrumental sounds and musical pieces in the test set of the salkh2100 dataset.
This dataset contains response data collected from experiments evaluating the similarity of instrument sounds, along with configuration information for the test sets used in the experiments. Below is a description of the files and directories included.

## Directory Structure

- `./csvs/`
  - Contains the response data from participants in the experiment.
- `./sample_configs/`
  - Stores JSON files detailing the configuration of each test set's samples.

---

## File Descriptions

### 1-1. `./csvs/inst_sim_abx_answers.csv`

This file contains response data from subjects (`subject_id`) who participated in the experiment. Each subject was asked to evaluate which of two samples, Sample A (`sample_a`) or Sample B (`sample_b`), was more similar to the reference sound (`reference`). The evaluation was based on four criteria: **Timbre**, **Rhythm**, **Melody**, and **Overall** similarity. They were allowed to select N/A from up to two perspectives except for **Overall**.

#### Column Descriptions
- `ex_name`: Experiment ID
- `subject_id`: ID of the subject
- `reference`: Path to the reference
- `sample_a`: Path to the sample A
- `sample_b`: Path to the sample B
- `answer_timbre`: Choice based on timbre similarity (A+ or A- or B+ or B- or N/A)
- `answer_rhythm`: Choice based on rhythm similarity (A+ or A- or B+ or B- or N/A)
- `answer_melody`: Choice based on melody similarity (A+ or A- or B+ or B- or N/A)
- `answer_total`: Overall similarity choice (A+ or A- or B+ or B-)
- `choice_time`: Time taken to make a choice (milliseconds)

### 1-2. `./csvs/inst_sim_abx_answers_XAB.csv` and `./csvs/inst_sim_abx_answers_XYC.csv`
These are split from `./csvs/inst_sim_abx_answers.csv` into two parts.
We made 2 types of sample sets, test 1 (XAB) and test 2 (XYC).
In test 1 (XAB), we randomly selected three different music tracks and captured 5-second segments for each.
In test 2 (XYC), Y is the different time segment from the same music track as X. C is from the different music track from X. The file `./csvs/inst_sim_abx_answers.csv` is all result containing both XAB and XYC, the file `./csvs/inst_sim_abx_answers_XAB.csv` only contains the results for XAB, and `./csvs/inst_sim_abx_answers_XYC.csv` only contains the results for XYC.


### 2. `./sample_configs/dict_triplet_202404.json` and `./sample_configs/dict_triplet_202407.json`

This file contains the configuration of samples in each test set in JSON format. Each test set consists of multiple instrument categories (e.g., drums, bass), and for each category, there are three samples: Sample X, Sample Y, and Sample C.

#### Format
- This configuration has the following structure.
Test Set Number
└── Sample Set Number
    └── Test Type ("test 1" or "test 2")
        └── Instrument ("drums", "bass", "piano", "guitar", "residuals", "mix")
            └── Sample type ("X", "A", "B", "Y", "C")
                ├── ID
                ├── seg
                ├── filename
                ├── sr
                ├── index_s
                └── index_e

- Each category includes Sample X, Sample A, and Sample B, or Sample X, Sample Y, and Sample C, with the following information provided for each sample:
  - `ID`: ID of the slakh 2100 dataset
  - `seg`: Segment number
  - `filename`: File name to be listed in the csv file
  - `sr`: Sampling rate (Hz)
  - `index_s`: Start index of the sample
  - `index_e`: End index of the sample
The number of start/end seconds can be calculated by index_{s, e}//sr.
If you save the audio segment using the above information in path=“set$no_set/$no_sample/$inst/$filename”, it will correspond to the csv file.
