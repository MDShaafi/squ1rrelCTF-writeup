# PYC Fun

You'll never be able to break into my secret Java coffee nut stash!

**File:** ([pyc_fun.pyc](pyc_fun.pyc))

**Type:** Reverse Engineering



# Solutions
First things first I noticed that it was a .pyc file. These sort of files are like bytecode versions of the python files. So I went ahead and tried to decompile it. I prefer to use pycdc a reliable python decompiler which normally is very trustworthy EXCEPT......

![pycdc_screenshot.png](pycdc_screenshot.png)

Due to this file being compiled in Python version 3.11 results were not so good. Mortified, I tried a few other python decompilers to come up with similar incomplete results. After close to an hour I figured might as well bruteforce. :)

```python

while True:

    
    for ch in word_array:
        password_string = ""
        password_string = ''.join(password)
        print(ch)
        count = count+1
        password_string = password_string+ch
        print(password_string)

        process = subprocess.Popen(["python", "-u", pyc_file_path], stdin=subprocess.PIPE, stdout=subprocess.PIPE, stderr=subprocess.PIPE, text=True)

    
        output, error = process.communicate(input=password_string)

        # output
        if output:
            print("Output:", output.strip())
            if output.strip()=="Correct!":
                print("BREAAAKKKKK")
                password.append(ch)
                break

        # error
        if error:
            print("Error:", error.strip())

        if count ==100:
            break 

    # finsh
    if count ==10:
        break 


print("Script execution completed.")


```

Built a simple python script to bruteforce the .pyc file till I got the final answer.

**Flag:** sq1urrel{pyc_r3v_1s_fun_56ja4ft}    

Finalizar !!

