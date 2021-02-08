# Coursera 
Python for everyone
--------------------------------------------------------------------------------------------------------------------------------------------
5.2 Write a program that repeatedly prompts a user for integer numbers until the user enters 'done'. Once 'done' is entered, 
print out the largest and smallest of the numbers. If the user enters anything other than a valid number catch it with a try/except and 
put out an appropriate message and ignore the number. Enter 7, 2, bob, 10, and 4 and match the output below.5.2 Write a program that repeatedly
prompts a user for integer numbers until the user enters 'done'. Once 'done' is entered, print out the largest and smallest of the numbers. 
If the user enters anything other than a valid number catch it with a try/except and put out an appropriate message and ignore the number. 
Enter 7, 2, bob, 10, and 4 and match the output below.

# Code

    largest = None
    smallest = None
    while True:
        num = input("Enter a number: ")
        if num == "done" : break
    
    
        try:
            fnum = int(num)
        except:
            print("Invalid input")
            continue
        # Largest
        if largest is None:
            largest = fnum
        elif fnum <= largest:
            largest = largest
        else:
            largest = fnum
        
        
        # Smallest    
        if smallest is None:
            smallest = fnum        
        elif fnum >= smallest:
            smallest = smallest
        else:
            smallest = fnum
        
    print("Maximum is", largest)
    print("Minimum is", smallest)




--------------------------------------------------------------------------------------------------------------------------------------------
7.2 Write a program that prompts for a file name, then opens that file and reads through the file, looking for lines of the form:

ex) X-DSPAM-Confidence:    0.8475

Count these lines and extract the floating point values from each of the lines and compute the average of those values and produce an output as shown below. 
Do not use the sum() function or a variable named sum in your solution.
You can download the sample data at http://www.py4e.com/code3/mbox-short.txt when you are testing below enter mbox-short.txt as the file name

# Code

    fname = input("Enter file name: ")
    fh = open(fname)
    counts = 0
    not_count = 0
    num = 0
    tot = 0

    for line in fh:
        counts += 1
        if not line.startswith("X-DSPAM-Confidence:"): 
            not_count += 1
            continue
        ind = line.find(':')
        num = line[ind+1:].strip()
    
        tot += float(num)
        
    tot_count = counts - not_count

    average = tot/tot_count
    print("Average spam confidence:",average)





--------------------------------------------------------------------------------------------------------------------------------------------
10.2 Write a program to read through the mbox-short.txt and figure out the distribution by hour of the day for each of the messages. 
You can pull the hour out from the 'From ' line by finding the time and then splitting the string a second time using a colon.

ex) From stephen.marquard@uct.ac.za Sat Jan  5 09:14:16 2008

Once you have accumulated the counts for each hour, print out the counts, sorted by hour as shown below.


# Code
    name = input("Enter file:")
    if len(name) < 1 : name = "mbox-short.txt"
    handle = open(name)
    hours = list()


    for line in handle:
        line = line.rstrip()
        words = line.split()
        if len(line) < 1:
            continue
        if words[0] != 'From':
            continue
        time = words[-2]
        time = time.split(':')
        hours.append(time[0])
    

    di = dict()    
    for h in hours:
        di[h] = di.get(h,0)+1        



    tup = sorted( [   (k,v) for k,v in di.items()  ] )

    for k,v in tup:
        print(k,v)
    

