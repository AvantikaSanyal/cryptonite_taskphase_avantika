# PRINTING VARIABLES
pwn.college{8UOdwHw4Ww8xZWUCPngckAL51m9.ddTN1QDLykzN0czW}

According to the example given I first tried 
   echo FLAG
   It just printed "FLAG"
So I according to the next example I tried: ($ is used to access variables)
  echo $FLAG

  # SETTING VARIABLES
  pwn.college{k4RAwwxfxGaGfQV7GrVUYNe8bVt.dlTN1QDLykzN0czW}
  This one was fairly simple, we were asked to set the value of the variable PWN to COLLEGE.
  According to the example i did PWN=COLLEGE (no spaces in between) and got my flag

  # MULTI WORD VARIABLES
  pwn.college{4JrQjFnSDgEV7v8i-a3ngH06VzC.dBjN1QDLykzN0czW}

  Here we needed to set the variable PWN to COLLEGE YEAH and we did that by simply doing 
     PWN="COLLEGE YEAH"

 # READING INPUT 
 pwn.college{YcE-qy6xNDBoQ1eUkY4uo1kO7T8.dhzN1QDLykzN0czW}
 i simply did read PWN
 entered the value that is needed to be stored in PWN that is college

 # READING FILES
 the challenge asked us to read /challenge/read_me into the variable PWN
  so i did "read PWN </challenge/read_me"
