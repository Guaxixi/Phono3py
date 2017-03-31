# Phono3py Compile tips on Mac OS

First, compile the newest version of Phonopy. 

Change the setup.cfg to below: 

`[install]`

`prefix= `


That's for using the `prefix --user`. And then just type `python setup.py install --user`

`phonopy` will be installed under `/Users/$USER/Library/Python/2.7/bin/` (if you use python2.7). Export this `PATH` in your `bash_profile` if it's not already there. 

The `PYTHONPATH` will be under `/Users/ruoxi/Library/Python/2.7/lib/python/site-packages/` 

Then download the newest version of `phono3py` from the its website. Change the setup.cfg to the same as above. Before compiling, you need to compile LAPACKE on your computer. 

In your setup.py, include your LAPACKE path, for example for me:

`if platform.system() == 'Darwin':`
    
    `include_dirs += ['/Users/ruoxi/Desktop/Software/lapack-3.7.0/LAPACKE/include']
    
    extra_link_args_lapacke = ['/Users/ruoxi/Desktop/Software/lapack-3.7.0/liblapacke.a']`

For myself, I couldn't compile with the gcc flag `fgopenmp` or `lgomp`, so I just deleted these flags in the setup.py file, and then it works for me. If you could compile without doing this, just forget about this. 

And then, `python setup.py install --user`

Your excutable will be under `/Users/$USER/Library/Python/2.7/bin/`. 

The `PYTHONPATH` will be under `/Users/ruoxi/Library/Python/2.7/lib/python/site-packages/` 

Add the PYTHONPATH to your `bash_profile`. 

Then type `phonopy` and `phono3py`, see if it works. 


No need to delete phonopy library, you can leave it both there. I assume when you run phonopy it will automatically goes into either to look for the module. 
But I didn't check that myself. 


