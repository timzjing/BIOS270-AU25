# Write-up 1

**Name:** Tim Jing
**Student ID:** timjing
**Date:** 11/11/2025  

---

## Overview

This writeup covers setup.md and environment.md. 

---

## Content

#### Setup.md
1. Three jobs will be submitted. This is becuase the job indicates --array=0-2, and each index represents one SLURM job.

2. The if statement checks the line number of `data.txt` and ensures that each of the 3 SLURM jobs receives 1/3rd of the lines to process, based on whether the line number % 3 = the index of the job in the array.

3. Each .out file will contain "line_number: value_of_line" where the line_number % 3 = the index of the job.


## Acknowledgement
Collaborator: N/A
