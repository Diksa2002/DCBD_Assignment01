# DCBD_Assignment01
# Analyzing Publication Metadata via RPC

**Name:** Diksa Pal Chowdhury  
**Roll No:** MDS2022518  
**Course:** Distributed Computing and Big Data  
**Assignment:** Analyzing Publication Metadata via RPC  

---

## Overview

This project implements a distributed MapReduce-style pipeline to analyze publication metadata fetched from a remote RPC server. The program retrieves titles of 1000 publications, extracts the first word of each title, and identifies the top 10 most frequent first words.

---

## Approach

- **Login:** Authenticates with the RPC server using the student ID to obtain a secret key.
- **Map Phase:** Splits the 1000 filenames across multiple CPU workers. Each worker fetches publication titles from the server and extracts the first word.
- **Reduce Phase:** Merges all worker results into a single word frequency counter.
- **Verify:** Submits the top 10 first words to the server for evaluation.

---

## Files

| File | Description |
|------|-------------|
| `run.py` | Main Python script implementing the MapReduce pipeline |
| `requirements.txt` | Python dependencies |
| `Dockerfile` | Docker container configuration |

---

## Requirements

- Python 3.11
- `requests` library

Install dependencies:
```bash
pip install -r requirements.txt
```

---

## How to Run

### Locally
```bash
python run.py
```

### Using Docker
```bash
# Build the image
docker build -t dcbd-assignment .

# Run the container
docker run dcbd-assignment
```

---

## Result

```
Top 10 First Words:
['Advanced', 'Analytical', 'Comprehensive', 'Automated', 'Distributed',
 'Dynamic', 'Fundamental', 'Heuristic', 'Experimental', 'Global']

Verification Result:
{'correct': True, 'message': 'Congratulations! You found all top 10 first words.', 'score': 10, 'total': 10}
```

**Score: 10/10** ✅
