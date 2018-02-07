# Linux GPU Commands for Data Science/ML

Launches jupyter notebook
# gpu-compute6.cs.duke.edu
```
~/.local/bin/jupyter-notebook
```

Launching web browser 
```
Jupyter: 
x-www-browser http://localhost:8888/tree/

TensorBoard: 
x-www-browser http://localhost/6006
```




Move file to GPU 
```
pscp .\patient_data.p ssh50@linux.cs.duke.edu:/home/home2/ssh50/patient-nlp
```
Add info about screening 
Attaching/removing screens 


1. Start a screen 
```
screen -S <screenname>
```
2. Come out of the screen (detach)
```
Ctrl-A + D: 
```
2. Seeing list of screens 
```
screen -ls
```

3. Removing screen
```
Ctrl-A K (inside the screen)
```

4. Going into the screen
```
screen -r <screenname> 
```

See GPU usages 
```
nvidia-smi
```

Pickle 
https://wiki.python.org/moin/UsingPickle

