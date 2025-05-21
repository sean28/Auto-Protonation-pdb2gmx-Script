# ⚙️ An auto protonation-pdb2gmx run script
<div style="text-align: justify"> The pdb2gmx command of GROMACS when using GROMACS for molecular dynamics simulation, the first command to be used is generally pdb2gmx. This command converts PDB molecular files into GROMACS' unique gro molecular structure file type, and generates molecular topology files at the same time. However, in the process of generating topology files, a protonation process is required, which can define the protonation options of each residue. This step is too cumbersome, so we made this script to auto run protonation for pdb2gmx to prevent dazzle. </div>
<div style="text-align: justify"> <br> </div>
<div style="text-align: justify"> The expect module of Perl is mainly used to practice this function, an example is as follows: </div>

```
#!/usr/bin/perl
use expect;
$exp->expect($timeout,-re=>"Which LYSINE" => sub { $exp->send("1\n"); exp_continue; });      #LYS option
$exp->expect($timeout,-re=>"Which ASPARTIC" => sub { $exp->send("0\n"); exp_continue; });    #ASP option
$exp->expect($timeout,-re=>"Which GLUTAMIC" => sub { $exp->send("0\n"); exp_continue; });    #GLU option
$exp->expect($timeout,-re=>"Which HISTIDINE" => sub { $exp->send("1\n"); exp_continue; });   #HIS option
$exp->interact()
```

The complete automation script is downloaded [here](https://drive.google.com/file/d/1ln_jsnAFGv4qk3abEPBiM5vrZJHcEnf5/view?usp=sharing).
Please contact the author for use permission and the decompression password.

<div style="text-align: justify"> Please note that before executing this script, you need to know the protonation options of each residue. It is recommended to use <a href="https://github.com/mms-fcul/PypKa">pypka method</a> to obtain protonation information. </div>
