---
keywords: fastai
description: My personal notes for the fast.ai live coding session week 1.
title: Live Coding Session 1
toc: true 
badges: false
comments: true
categories: [live-coding]
nb_path: _notebooks/2022-08-05-fastai-livecoding-1.ipynb
layout: notebook
---

<!--
#################################################
### THIS FILE WAS AUTOGENERATED! DO NOT EDIT! ###
#################################################
# file to edit: _notebooks/2022-08-05-fastai-livecoding-1.ipynb
-->

<div class="container" id="notebook-container">
        
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Relevant-Material">Relevant Material<a class="anchor-link" href="#Relevant-Material"> </a></h1><p><a href="https://forums.fast.ai/t/live-coding-1/96649">Live Coding Session 1 (Forum Topic)</a>
{% include youtube.html content='<a href="https://youtu.be/56sIyFjihEc">https://youtu.be/56sIyFjihEc</a>' %}</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Disclaimer">Disclaimer<a class="anchor-link" href="#Disclaimer"> </a></h1><p>These are my personal notes. They are not meant to be a comprehensive summary of the live coding session, but rather the things I wanted to note down for myself to refer to at a later point.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Notes">Notes<a class="anchor-link" href="#Notes"> </a></h1><h2 id="Prerequisites">Prerequisites<a class="anchor-link" href="#Prerequisites"> </a></h2><ul>
<li>Install Windows Subsystem for Linux (WSL) by typing into Powershell (run as admin): <code>wsl --install</code><ul>
<li>For more details refer to <a href="https://docs.microsoft.com/en-us/windows/wsl/install">guide by Microsoft</a></li>
</ul>
</li>
<li>Check whether Python and Jupyter are installed: <code>python</code> and <code>jupyter</code><ul>
<li>Output (e.g. for Python) should be: <code>Command 'python' not found</code> </li>
<li>There probably is a system version of Python. You do not want to be using this since it may interfere with the OS behavior.</li>
</ul>
</li>
</ul>
<h2 id="Install-conda/mambaforge-manually">Install conda/mambaforge manually<a class="anchor-link" href="#Install-conda/mambaforge-manually"> </a></h2><ol>
<li>Make downloads directory inside home directory: <code>mkdir downloads</code></li>
<li>Download mambaforge: <code>wget https://github.com/conda-forge/miniforge/releases/latest/download/Mambaforge-Linux-x86_64.sh</code></li>
<li>Install mambaforge using bash: <code>bash Mambaforge-Linux-x86_64.sh</code><ul>
<li>To ensure python environment is set up when starting terminal: <code>Do you wish the installer to initialize Mambaforge by running conda init? [yes|no]</code> &rarr; <code>yes</code></li>
</ul>
</li>
<li>After installing and restarting shell, terminal should mention <code>(base)</code> and <code>which python</code> should show a python directory in the mambaforge directory</li>
</ol>
<h2 id="Install-conda/mambaforge-with-bash-script-from-fastai/fastsetup">Install conda/mambaforge with bash script from fastai/fastsetup<a class="anchor-link" href="#Install-conda/mambaforge-with-bash-script-from-fastai/fastsetup"> </a></h2><ol>
<li>If you followed steps to manually install conda/mambaforge:<ul>
<li>Remove mambaforge from home directory: <code>rm -rf mambaforge</code> </li>
<li>Remove mambaforge installer from downloads directory: <code>rm -rf</code></li>
<li>Restart shell</li>
</ul>
</li>
<li>Go to <a href="https://github.com/fastai/fastsetup">fastsetup github repo</a> and click on setup-conda.sh. Subsequently click on raw and copy url. Download it: <code>wget https://raw.githubusercontent.com/fastai/fastsetup/master/setup-conda.sh</code></li>
<li>Run it: <code>bash setup-conda.sh</code> or <code>./setup-conda.sh</code><ul>
<li>If you get <code>Permission Denied</code> then:<ul>
<li>Inspect permissions: <code>ls -l</code> (output needs to contain 'x' which stands for permission to execute)</li>
<li>Change permission: <code>chmod u+x setup-conda.sh</code></li>
</ul>
</li>
</ul>
</li>
</ol>
<h2 id="Install-other-packages-with-mamba">Install other packages with mamba<a class="anchor-link" href="#Install-other-packages-with-mamba"> </a></h2><ul>
<li>Python libraries can be installed with: conda, pip, mamba<ul>
<li>conda vs mamba: 2 ways of doing same thing, compatible with each other, mamba is faster</li>
<li>prefer to use mamba, but usually documentation refers to conda (more established, around longer)</li>
<li>advantage of conda/mamba over pip is that the dependencies are also installed correctly. If you use pip to install pytorch for instance, you need to install other stuff as well, whereas conda/mamba take care of installing everything you need correctly.</li>
</ul>
</li>
<li>Never install stuff through <code>apt</code>, that is system stuff</li>
</ul>
<ol>
<li>Install ipython: <code>mamba install ipython</code></li>
<li>Install pytorch:<ol>
<li>Go to <a href="pytorch.org">pytorch.org</a>  &rarr; Get Started &rarr; Start Locally</li>
<li>Pick options: Stable, Linux, Conda, Python, CPU</li>
<li>Copy command, paste into terminal, change conda to mamba: <code>mamba install pytorch torchvision torchaudio cpuonly -c pytorch</code><ul>
<li><code>-c pytorch</code> refers to the channel of pytorch </li>
<li>check if installed correctly by starting <code>ipython</code> and subsequently typing <code>import torch</code>.</li>
</ul>
</li>
</ol>
</li>
<li>Install jupyerlab: <code>mamba install jupyterlab</code><ul>
<li>Start Jupyter Lab: <code>jupyter lab</code></li>
<li>This will start jupyter server. It will try to open browser, but there is no browser in Ubuntu, so it will give error. But link that is returned in Terminal can be <kbd>Control</kbd>+clicked to open browser in Windows.</li>
<li>If you do not want the error, add flag: <code>jupyter lab --no-browser</code></li>
</ul>
</li>
</ol>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Useful-tips/commands-in-Linux">Useful tips/commands in Linux<a class="anchor-link" href="#Useful-tips/commands-in-Linux"> </a></h2><ul>
<li>Check where Python is installed: <code>which python</code></li>
<li>Print working directory you are in: <code>pwd</code></li>
<li>Navigate to home directory: <code>cd</code> or <code>cd ~</code></li>
<li>Make directory: <code>mkdir [directory name]</code></li>
<li>Delete directory (recursive and force delete): <code>rm -rf [directory name]</code></li>
<li>Move directory: <code>mv</code></li>
<li>List contents of directory <code>ls [-flags]</code>
  Flags<ul>
<li>Long form: <code>l</code></li>
<li>Human readable: <code>h</code></li>
<li>All (i.e. including hidden ones): <code>a</code></li>
<li>Sorted by date modified: <code>t</code></li>
<li>Possible to combine flags, e.g.: <code>ls -lhat</code> </li>
</ul>
</li>
<li>Look at a text file: <code>less [filename]</code></li>
<li>Restart shell: <code>sudo -u [user] -i</code></li>
<li>Change permission: <code>chmod u+x [filename]</code> (u=user, x=execute permission)</li>
<li>Close terminal program: <kbd>Control</kbd>+<kbd>D</kbd></li>
<li>Shortcut to run command: press <kbd>UP</kbd> arrow to cycle through previous commands<ul>
<li>All your terminal inputs are stored in the home folder in a file named <code>.bash_history</code>. This is convenient for creating bash scripts. Note that <code>.bash_history</code> is overwritten. If you have multiple bash sessions, only last one will survive.</li>
</ul>
</li>
<li>Search through your previous terminal commands: <kbd>Control</kbd>+<kbd>R</kbd></li>
<li>Run last command starting with some letters: <code>![letters]</code><ul>
<li>e.g. if last command you ran starting with <code>ju</code> was <code>jupyter lab --no-browser</code>, then <code>!ju</code> would run that command</li>
</ul>
</li>
<li>Run last command: <code>!!</code><ul>
<li>can use <code>echo</code> to print it</li>
</ul>
</li>
<li>Jump to:<ul>
<li>end of line: <kbd>Control</kbd>+<kbd>E</kbd></li>
<li>start of line: <kbd>Control</kbd>+<kbd>A</kbd></li>
<li>end/start of a word : <kbd>Control</kbd>+<kbd>LEFT</kbd>/<kbd>RIGHT</kbd></li>
</ul>
</li>
<li>Define alias (i.e. a shortcut for a command): <code>alias [alias]="[command]"</code><ul>
<li>e.g. alias jl="jupyter lab --no-browser"</li>
<li>if you want it to persist across sessions, need to add it to <code>.bashrc</code> or to <code>.bash_aliases</code></li>
</ul>
</li>
</ul>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Useful-tip-for-ipython">Useful tip for ipython<a class="anchor-link" href="#Useful-tip-for-ipython"> </a></h2><ul>
<li>By pressing <kbd>TAB</kbd> after typing a library name, you get to see all the functions (including arguments), submodules, etc.</li>
</ul>

</div>
</div>
</div>
</div>
 
