# Generalized BPE Segmentation

This is a manual for the usage of c++ implementation of Generalized BPE Segmentation.
The source code is contained in the file `gbpe.cpp`. 

## Build
Run the command below to get an executable file `gbpe`:
```bash
g++ gbpe.cpp -o gbpe
```

## Train
```bash
gbpe -bpe input_file [input_format] [measure] [merge_times] output_file
```
`input_file`: tokenized plain text or vocabulary file according to the `input_format` parameter. 

`input_format`: `0` for plain text input, `1` for vocabulary input with each line containing a word-frequency pair.

`measure`: `0` for frequency-weighted FRQ'-BPE, `1` for frequency-weighted AV'-BPE, `2` for frequency-weighted DLG'-BPE, `10` for unweighted FRQ-BPE, `11` for unweighted AV-BPE, `12` for unweighted DLG-BPE,
`24, 34, ..., 104` for `0.1AV'-BPE + 0.9DLG'-BPE, 0.2AV'-BPE + 0.8DLG'-BPE, ..., 0.9AV'-BPE + 0.1DLG'-BPE`.

`merge_times`: an integer for the number of merge operations.

`output_file`: the file to save the segmented words appearing in `input_file`.

Two additional file `vocab.txt` and `vocab.substring.txt` will be automatcially generated after running the command. 
`vocab.txt` contains the vocabulary of `input_file`, `vocab.substring.txt` contains the ordered merged pairs with their goodness score.

## Apply
```bash
gbpe -bpeseg input_file vocab.substring.txt output_file
```
`input_file`: tokenized corpus to be segmented.

`output_file`: corpus segmented with `@@` tokens.

## Note
All the input and output files should be encoded as UTF-8.






