# Linux GPU Commands for Data Science/ML

Launches jupyter notebook

```
~/.local/bin/jupyter-notebook
```

Launching web browser 
```
x-www-browser http://localhost:8888/tree/
```




Move file to GPU 
```
pscp .\patient_data.p ssh50@linux.cs.duke.edu:/home/home2/ssh50/patient-nlp
```
Add info about screening 
Attaching/removing screens 


1. Start a screen 
```
screen -S screenname
```
Ctrl-A + D: come out of the screen


2. Seeing list of screens 
screen -ls: see list of screens 


3. Removing screen
Ctrl-A K inside the screen 

4. Going into the screen
screen -r screenname 




See GPU usages 
```
nvidia-smi
```
