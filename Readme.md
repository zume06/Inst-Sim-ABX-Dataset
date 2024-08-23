# Instrumental Similarity ABX Dataset

This dataset contains response data collected from experiments evaluating the similarity of instrument sounds, along with configuration information for the test sets used in the experiments. Below is a description of the files and directories included.

## Directory Structure

- `./csvs/`
  - Contains the response data from participants in the experiment.
- `./sample_configs/`
  - Stores JSON files detailing the configuration of each test set's samples.

---

## File Descriptions

### 1. `./csvs/inst_sim_abx_answers.csv`

This file contains response data from subjects (`userId`) who participated in the experiment. Each subject was asked to evaluate which of two samples, Sample A (`SampleA`) or Sample B (`SampleB`), was more similar to the reference sound (`Reference`). The evaluation was based on four criteria: **Timbre**, **Rhythm**, **Melody**, and **Overall** similarity.

#### Column Descriptions
- `ex_name`: Experiment ID
- `userId`: ID of the subject
- `Reference`: Path to the reference
- `SampleA`: Path to the sample A
- `SampleB`: Path to the sample B
- `choice_answerTimbre`: Choice based on timbre similarity (A+ or A- or B+ or B-)
- `choice_answerRhythm`: Choice based on rhythm similarity (A+ or A- or B+ or B-)
- `choice_answerMelody`: Choice based on melody similarity (A+ or A- or B+ or B-)
- `choice_answerTotal`: Overall similarity choice (A+ or A- or B+ or B-)
- `choice_time`: Time taken to make a choice (milliseconds)

### 2. `./sample_configs/dict_triplet_202404.json`

This file contains the configuration of samples in each test set in JSON format. Each test set consists of multiple instrument categories (e.g., drums, bass), and for each category, there are three samples: Sample X, Sample Y, and Sample C.

#### Format
- Each test set contains multiple categories (e.g., `drums`, `bass`).
- Each category includes Sample X, Sample Y, and Sample C, with the following information provided for each sample:
  - `ID`: Identifier for the sample
  - `seg`: Segment number
  - `filename`: Name of the audio file
  - `sr`: Sampling rate (Hz)
  - `index_s`: Start index of the sample
  - `index_e`: End index of the sample
