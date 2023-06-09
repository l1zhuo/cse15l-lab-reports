# **CSE15L Lab Report 3**

---

## Options for `grep` command

All sources cited from [https://linuxcommand.org/lc3_man_pages/grep1.html](https://linuxcommand.org/lc3_man_pages/grep1.html)(Docummentation on Linux Command)

---



##  `grep -r` ##



(source cited above on `grep -r`)

### Example 1  ###

```

$grep -r "base pair" ./technical/plos

#Output

technical/plos/journal.pbio.0020190.txt:        sequence, which is a specific series of eight base pairs in the DNA of the bacterial
technical/plos/journal.pbio.0020190.txt:        chromosomes, on the order of one or two thousand base pairs of DNA (or less—their length is
technical/plos/journal.pbio.0020223.txt:        Watson-Crick base pairing, the proximity of the synthetic reactive groups elevates their

```

In example 1, the `grep -r` option recursively read through all files in the path `./technical/plos` and returns lines that contain the string `"base pair"`. This is useful because I don't have to manually input every file name as the argument for `grep`, instead I can just use the option to find all line that contain the specific string in `/plos`. 

### Example 2  ###


```

$grep -r  "the conclusions" ./technical/plos

#Output

./technical/plos/journal.pbio.0020150.txt:        But the hypotheses that can be tested and the conclusions that can be drawn are still
./technical/plos/journal.pbio.0020150.txt:        the conclusions that are valid for groups. This makes fMRI an unlikely tool for job 
./technical/plos/pmed.0020088.txt:        We cannot rely entirely on peer review to detect bias in the conclusions of an article,
./technical/plos/pmed.0020235.txt:        birth order also limits the conclusions that can be drawn. These limitations are countered, 
./technical/plos/pmed.0020272.txt:        research findings would therefore seem to concern the conclusions, and Ioannidis's claim    
./technical/plos/pmed.0020272.txt:        means the conclusions reported should be more rather than less likely to be true. But    

```

Similar to example 1, the `grep -r` option recursively read through all files in the path `./technical/plos` and returns lines that contain the string `"the conclusions"` in it and the path to the file with that line. This is useful because the `-r` option allows `grep` to take in directories as arguments instead of only files. Also, this allows for quick search in files that may contain the pattern string without specifying which file to look for. 

---


##  `grep -l` ##



(source cited above on `grep -l`)

### Example 1  ###

```

$grep -l "base pair" ./technical/plos/*.txt

#Output

./technical/plos/journal.pbio.0020190.txt
./technical/plos/journal.pbio.0020223.txt

```

`grep -l` option controls the output of a default `grep`. Specifically, it stops the printing of the matched lines (input), but only prints out the path to files with matched lines. This means that in this example, the `grep` outputs all files' path in `/plos` that contain the text `"base pair"`. This is useful because this allows me to quickly check how many files, or which files that contain the string that I am looking for.


### Example 2  ###


```

$grep -l "the conclusions" ./technical/plos/*.txt

#Output

./technical/plos/journal.pbio.0020150.txt
./technical/plos/pmed.0020088.txt
./technical/plos/pmed.0020235.txt
./technical/plos/pmed.0020272.txt

```

Similar to example 1, it prints out only the path to the files that contain the pattern indicated  with "`the conclusions"` . This allows us to see how many files contain the matching pattern given a path, and what the path of those files are without knowing the specific context. 

---


##  `grep -i` ##



(source cited above on `grep -i`)

### Example 1  ###

```

$ grep -i  "dna" ./technical/plos/*.txt

#Output

./technical/plos/journal.pbio.0020013.txt:        cell surface receptor modulation, secretion, DNA repair, transcriptional regulation,
./technical/plos/journal.pbio.0020013.txt:        DNA damage) in a manner that is intimately linked to the ubiquitin–proteasome system. This
./technical/plos/journal.pbio.0020028.txt:        been largely disappointing. Antisense is a single strand of RNA or DNA, complementary to a
./technical/plos/journal.pbio.0020028.txt:        eye for patients with HIV. Vitravene is actually a DNA antisense drug, which binds to viral
./technical/plos/journal.pbio.0020028.txt:        DNA, though, says Usman, “it's unclear whether it actually works by an antisense    
./technical/plos/journal.pbio.0020028.txt:        drug, Genasense. Genasense is a DNA-based treatment that targets Bcl-2, a protein expressed
./technical/plos/journal.pbio.0020035.txt:        keto group modification, so the programming would (in principle) be simple. The DNA 
./technical/plos/journal.pbio.0020035.txt:        the DNA sequence of the gene set for the complex polyketide erythromycin, made by a 
./technical/plos/journal.pbio.0020035.txt:        the program for the PKS is hardwired into the DNA and expressed in a linear array of active
./technical/plos/journal.pbio.0020040.txt:        irradiation-induced DNA damage. The authors studied the expression of two p53-upregulated
... (more output not copied over to save space)


```


`grep -i` option controls how the `grep` interprets the pattern. It allows the `grep` to ignore case of the pattern when searching for a match. This means in example 1, the `grep` is doing a search for any lines that contain any case combination of `dna`. This is useful because it allows us to do a general search of a word that we don't really care about the case of it. 

### Example 2  ###


```

$grep -i  "dna and rna" ./technical/plos/*.txt

#Output

./technical/plos/journal.pbio.0020302.txt:        biomass: the hardware of life (Lehninger 1975, p 21). The DNA and RNA software of life is

```

Similar to example 1, the `grep`ignores the case of "`dna and rna"` to find all matching lines that contain those sequence of alphabets. This is useful because previously, the default `grep` finds the matching lines and output them word for word. However, if we are not looking for the exact match, but just the same phrase, we can use this option to help us search more precisely.


---

##  `grep -c` ##



(source cited above on `grep -c`)

### Example 1  ###

```

$ grep -c "conclusion" technical/plos/*.txt

#Output

technical/plos/journal.pbio.0020001.txt:0
technical/plos/journal.pbio.0020010.txt:0
technical/plos/journal.pbio.0020012.txt:0
technical/plos/journal.pbio.0020013.txt:0
technical/plos/journal.pbio.0020019.txt:0
technical/plos/journal.pbio.0020028.txt:0
technical/plos/journal.pbio.0020035.txt:1
technical/plos/journal.pbio.0020040.txt:0
... (more output not copied over to save space)


```

`grep -c` option moderates the output so it only prints the number of lines that contain the specific pattern in a given file. It prints similarily to the `wc` command, but allows count lines on a specific pattern. In this example, the `grep -c` counts how many lines of each text file contain the matching pattern `"conclusion"` and output it. This is useful because if we are looking for how many times a specific word appeared in a text file, we can do it efficiently with this option without doing `wc` on a file direct of normal `grep`. E.g. `xargs wc < grep "conclusion" technical/plos/*.txt`. 

### Example 2  ###


```

$$ grep -c "number" technical/plos/pmed.0020242.txt


#Output

5

```

In example 2, the command counts number of lines that contain `"number"` in the file `"pmed.0020242.txt"`. This is useful because we don't have to go through saving the file from `grep` and use `wc` to count number of lines, instead we can quickly do it with `-c` option. This is also useful because this is another way for us to see if a string is contained in a file, and I'd say this way is cleaner than just do a normal `grep`.  

---

