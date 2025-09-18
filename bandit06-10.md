# Bandit level 06 -> 07 

description: The password for the next level is stored somewhere on the server and has all of the following properties:

    owned by user bandit7
    owned by group bandit6
    33 bytes in size

## STEPS 
```ls 
output: 
--- 
``` cd .. 
output: /home 
---
``` find -type f -size 33c -user bandit7 -group bandit6
output: andit6@bandit:/$ find -type f -size 33c -user bandit7 -group bandit6
find: ‘./sys/kernel/tracing/osnoise’: Permission denied
find: ‘./sys/kernel/tracing/hwlat_detector’: Permission denied
.
.
.
find: ‘./home/bandit28-git’: Permission denied
find: ‘./home/bandit29-git’: Permission denied
find: ‘./home/drifter8/chroot’: Permission denied
---
``` cd ..
output: / 
---
``` find -type f -size 33c -user bandit7 -group bandit6
output: 
...
./var/lib/dpkg/info/bandit7.password
...
--- 
``` cat ./var/lib/dpkg/info/bandit7.password
output: morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

**result:** morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

# Bandit 07 -> 08 

description:The password for the next level is stored in the file data.txt next to the word millionth 

## STEPS
1. checking whats inside de bandit7 folder
``` ls 
output: data.txt 
--- 
2. printing the data.txt: 
``` cat data.txt 
output: 
...
admiration's	bvoYElHq7qH0Ih9gVNSlDEWmNBg1Fgp5
metacarpi	iz1zJx7A7fT0wHbWaG2QgfF6RxOjxO8s
communique	V24m0stXPKp8Ox6RKMSHb3lsu8gqw1tx
beet	pcShD5F2Dp3yttqq2LyVxOfK3CoU0kFw
bloomed	TSDPVLXL2RwiqW1IUJYloLIQrvlTRia7
sidetracked	UiNbB0c2snVdCNgkKAjZX8p8TqdzlPnv
albacore	AVapPRDII66G17bO1XXPjxMQ6KyBYYMO
sorrowed	tGX8TOxvAO2iMYeAjA0aI1jMLxh0hpMv
Manson	i56bqCgO2LqXbRmFRoUCxYkuapWnTN
...
3. filtering the file: 
``` cat data.txt | grep millionth 
output: millionth	dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

password: dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

# Bandit 08 -> 09 
description: The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

## STEPS 
1. checking whats inside de folder 
``` ls 
output: data.txt 

2. printing the data.txt :
``` cat data.txt 
output: XLIyGDiAhBDFA9bxwymTQ8Dqm5YibqnK
qCJGPHoYzD6N3nLNyyKXxDgJZwF7j81j
u3u2A89W6wrNLaArSfEE0H79g3gImwne
SC5NNAB0eNxsXUOI1t1RwVdJIfRqJFzL
Dq6lTcnZO3PWzzEYDC8Cfwu4sPR4R47v
anovJBgvwRvdglX5PhYQCEhK8VuML28V
EVW5uJS3JPjKKhgGdFYkwf7IJxzW72sX
3PRLMUKYoKCLPW9mJBO6lwJ8YphI6uQV

3. removing duplicated lines with: 
``` sort data.txt | uniq -u 
output: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

password: 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

# Bandit 09 -> 10 

description: The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

## STEPS    
1. basic check
``` ls 
output: data.txt 

2. tried to extract the string with
``` cat data.txt | grep =====
output: grep: (standard input): binary file matches

3. using `strings to show ASCII in the data.txt: 
``` strings data.txt | grep ==== 
output: ========== theg
========== password
========== is
========== FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

password: FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

# Bandit 10 -> 11 

description: The password for the next level is stored in the file data.txt, which contains base64 encoded data

## STEPS 
1. basic check: 
``` ls 
output: data.txt 
2. using base64 directly: 
```base64 data.txt
output: VkdobElIQmhjM04zYjNKa0lHbHpJR1IwVWpFM00yWmFTMkl3VWxKelJFWlRSM05uTWxKWGJuQk9W
bW96Y1ZKeUNnPT0K
3. using base64 decode :
``` base64 -d data.txt
output: The password is dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

password: dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr
