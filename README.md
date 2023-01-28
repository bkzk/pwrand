# pwrand

Simple pseudo-random string generator based on entropy gathered from /dev/(u)random device. Using /dev/urandom as a source of entropy is default. If you feel paranoiac you can always switch to /dev/random which has a more conservative entropy calculation. 

As a curiosity. If you are wondering how many bits of entropy is already gathered by your system, look into: /proc/sys/kernel/random/entropy_avail.


### Installation

Clone it and move to your globally available paths or just use it.

    git clone https://github.com/bkzk/pwrand.git

    cd pwrand/
    install -m0755 pwrand /usr/local/bin/

### Usage

    $ pwrand -h
    Usage: 
      -u     - include uppercase letters
     -l     - include lowercase letters
     -d     - include digits
     -w     - include white spaces 
     -n     - include underline 
     -m     - include minus sign
     -s     - include other special characters
     -a     - equivalent for -uld, all alphanumeric characters (default) 
     -A     - include all printable characters 
     -P     - the number of displayed examples (default 12)
     -E     - show filtered entropy 
     -x N   - passwords length (default N=12)
     -v     - be more verbose
     -q     - be quiet, less verbose

#### Examples

By default, the script returns ten 12-char length strings consisting of upper and lower-case letters and numbers. Use some switches to change the length, number of lines, or type of characters.

    $ pwrand 
    Random generated 12-char length passwords

    78KuN3GXOMOg
    cuKpspsPv102
    NMexXyngq4rq
    W32LFTBwuDE2
    aL1Mb59SHXwr
    C9Zg2SXoHM0L
    LaCgkad3wKKw
    A2nhXQlgDlxM
    SxDmFWjIGZKv
    h3q7wZhVMLfT

To get all (-A) printable characters, 30 chars long, 5 lines

    pwrand -A -x 30 -P 5
    Random generated 30-char length passwords

    ?3fdH+c{XU{$bByn},qi7G1&wDSbx@
    Jcp:2GNf0d5/L:qCUcO;QV=V>[i-D(
    ;G!{rSRaibNWS)0.X8w)Z)[~[,0JJf
    N"a9.{fUTo{Tl7rRs+GY{[WiX"c@ z
    N'cgP,)PAU x|:r)YfO?]0NS,]uP.{

To get one line 320 chars long, eg. like for encrypting truecrypt volumes.

    # Please type at least 320 randomly chosen characters and then press Enter:

    $ pwrand -P 1 -x 320 -q
      f4g7hRPgJqj2BPGzNfrsZrZwaEV2Vgo15NOoxTG00HaxEa4tk2weVNmDFHrIRffiicL1thj7irYQhni4LbQmG6nTCXPxu7e3SQuxZClIAWxA0kILvbMpQl2sFC5oDTixMzLAoEwbMhq5oaW21ykEwxopZPFMS6mDLzxcfU0sDm6v9iYhvzJh6v77FGeDuwSxYMecbf8Ms3zlZ9Mm207YxhrIYW6M7ljGBzfVaBq8HIGTP0remrRbgd5SADj95yeaq4b6r8Ed1lLNorXfx0QAlX72eBS7Cg2xrN8tzgMvhJ7oUw4zDOyz0YM8Bhp1WDTz

Be more verbose.

    $ pwrand  -P 1 -A -x 24 -v
    > Password character groups in use:

     Uppercase       [ + ]
     Lowercase       [ + ]
     Numbers         [ + ]
     Minus           [ + ]
     Underline       [ + ]
     White Spaces    [ + ]
     Special Char.   [ + ]

    > Entropy: 24000 chars - after reading: 64887 bytes 
    > after filtering: 24000 chars

    Random generated 24-char length passwords

    v"5ZE|J^qps{s*}NDzlYA:*e

