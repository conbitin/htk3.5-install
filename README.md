# htk3.5-install

## 1. Pre-requirement install X11
<pre>
$ sudo apt-get install libx11-dev
</pre>

## 2. Download the HTK version of Linux/Unit
Go to [HTK download page](http://htk.eng.cam.ac.uk/download.shtml). But first, need to **register** (free)
At this time, HTK version is 3.5 beta(2).
Download both **HTK source code** and **HDcode page**.

## 3. Install HTK
<pre>
$ tar xzf HTK-3.5.beta-2.tar.gz
$ tar xzf HDecode-3.5.beta-1.tar.gz
</pre>

Go to each of following folders: **HTKLib**, **HLMLib**, **HTKTools**, **HLMTools**, **HTKLVRec** and install like below:
<pre>
$ cd HTKLib
$ make -f MakefileCPU all
$ make -f MakefileCPU install
</pre>
(If you want to compile CPU using MKL or NVIDIA GPUs, change **MakefileCPU** according **MakefileMKL**, **MakefileNVCC**)

## 4. Set PATH
After run all install command, one directory is created under htk, named: **bin.cpu**.
Need to set this directory as system-wide PATH. So, go to root directory and run:
<pre>
$ sudo gedit /etc/environment
</pre>
Add absolute path of **bin.cpu** directory in environment file and save it.
Now, make change affect:
<pre>
$ source /etc/environment
</pre>
And check what we do is correct or not
<pre>
$ echo $PATH
</pre>

## 5. Test HTK
When Install HTK in step 2, there is also directory inside htk directory, named **samples**. If not, got to [HTK download page](http://htk.eng.cam.ac.uk/download.shtml) to get it
<pre>
$ cd samples
$ cd HTKDemo
$ mkdir -p hmms/{tmp,hmm.{0,1,2,3}} proto accs test
$ ./runDemo configs/monPlainM1S3.dcf
</pre>
If test succeed, there is result like below:
<pre>
--------------------- Overall Results -----------------------
SENT: %Correct=0.00 [H=0, S=3, N=3]
WORD: %Corr=63.91, Acc=59.40 [H=85, D=35, S=13, I=6, N=1
=============================================================
</pre>





