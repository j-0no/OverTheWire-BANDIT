# Bandit level 00 -> 01 

description: The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

## STEPS
``` ls 
output: readme 
---
``` cat readme 
output: Congratulations on your first steps into the bandit game!!
Please make sure you have read the rules at https://overthewire.org/rules/
If you are following a course, workshop, walkthrough or other educational activity,
please inform the instructor about the rules as well and encourage them to
contribute to the OverTheWire community so we can keep these games free!

The password you are looking for is: ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

**result:** ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

# Bandit level 01 -> 02  

description: The password for the next level is stored in a file called - located in the home directory

## STEPS 
``` ls 
output: - 
--- 
cat <- 
output: 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

**result:** 263JGJPfgU6LtdEvgfWU1XP5yac29mFx

# Bandit level 02 -> 03 

description: The password for the next level is stored in a file called --spaces in this filename-- located in the home directory

## STEPS
``` ls 
output: --spaces in this file-- 
---
cat < "--spaces in this filename--" 
output: MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

**result:** MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

# Bandit level 03 -> 04 
description: The password for the next level is stored in a hidden file in the inhere directory.

## STEPS
``` ls 
output: inhere/ 
---
``` ls inhere/ 
output: 
--- 
``` cd inhere/
``` ls -a 
output: . .. ...Hiding-From-You 
--- 
``` cat ...Hiding-From-You 
output: 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

**result:** 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

# Bandit level 04 -> 05 a
description: The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.

## STEPS 
``` ls 
output: inhere/ 
--- 
``` cd inhere/ 
``` ls 
output: -file00  -file01  -file02  -file03  -file04  -file05  -file06  -file07  -file08  -file09
--- 
comment: now is just a matter of using ```ls <-file0X and fiding the file with the password
``` ls <-file07 
output:4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

**result:** 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

# Bandit level 05 -> 06 
description: The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

    human-readable
    1033 bytes in size
    not executable

## STEPS 
``` ls 
output: inhere/ 
--- 
``` cd inhere/ 
``` ls 
output: maybehere00  maybehere02  maybehere04  maybehere06  maybehere08  maybehere10  maybehere12  maybehere14  maybehere16  maybehere18
maybehere01  maybehere03  maybehere05  maybehere07  maybehere09  maybehere11  maybehere13  maybehere15  maybehere17  maybehere19
``` find -type f -size 1033c ! -executable
output: ./maybehere07/.file2
``` cat ./maybehere07/.file2
output: HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

**result:** HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

