# Week 5 Lab Report

## The 'grep' command: The Basics
- The grep command can be used in Linux-based terminals to filter through a file for a particular pattern of characters which is specified in the execution of the command.
    - The formatting of the grep command follows as is: grep -options "Character Pattern" fileToSearch.txt
    - Multiple file locations can be "grepped" by appending another file location to the command, or using the * operators. 
    - grep does not work on directories. 

## The 'grep' command: Option -i
- The -i option ignores case sensitivity. 
    - It is useful when the word you are searching for may be at the front of the sentence, and thus capitalized. 
    - Example 1: "California" 
        ```
        [cs15lfa22ks@ieng6-203]:skill-demo1:352$ grep -i "California" */*/*.txt
        technical/911report/chapter-11.txt:                California went on the watch for his like.
        technical/911report/chapter-13.4.txt:                chemistry, from California State University, Sacramento. Sufaat did not start on the
        technical/911report/chapter-13.4.txt:                reasons for sending Hazmi and Mihdhar to California do not seem especially      
        technical/911report/chapter-13.4.txt:                explanation for the California destination. The possibility that the two hijackers
        technical/911report/chapter-13.4.txt:                addresses-one in the United States ("possibly in California") and one in South  
        technical/911report/chapter-13.4.txt:                California." Intelligence report, interrogation of KSM, June 15, 2004.
        technical/911report/chapter-13.4.txt:                acclimate the hijackers to the United States, particularly San Diego, California."
        technical/911report/chapter-13.4.txt:                California, but Atta told him to discontinue this effort. Intelligence report,  
        technical/911report/chapter-13.4.txt:                his training in California, see FBI report of investigation, interview of Adnan 
        technical/911report/chapter-13.5.txt:            85. Hazmi and Mihdhar used their true names to obtain California driver's licenses  
        technical/911report/chapter-3.txt:                California (UNOCAL) to build a pipeline across the country. While there was probably
        ```
        - There are more results, but for the sake of simplicity they have been truncated. 
        - The `*/*/*.txt` simplifies into the directories of the current directories, then into the directories in those directories. Even if they may have more directories, they will not be accessed, since it was not specified by the command. 
    - Example 2: "south korea"
        ```
        [cs15lfa22ks@ieng6-203]:skill-demo1:358$ grep -i "south korea" */*/*.txt
        technical/911report/chapter-13.4.txt:                Khallad, Aug. 13, 2003; Apr. 5, 2004. According to Khallad, Thailand, South Korea,
        technical/911report/chapter-5.txt:                Thailand, South Korea, Hong Kong, or Malaysia, and using Yemenis who would not need
        technical/biomed/1472-6823-2-2.txt:          Jolla, CA; Sofia, Bulgaria; Seoul, South Korea and São
        technical/biomed/1472-6920-2-3.txt:        South Korea [ 5 ] and for a Turkish medical school [ 6 ] .
        ```
        - Even though I passed in "south korea" as an argument, it finds all instances of "South Korea" because it ignores cases. Were I to do the same command with no specified option, then I would receive no return result. 
    - Example 3: "war"
        ```
        [cs15lfa22ks@ieng6-203]:skill-demo1:358$ grep -i "war" */*/*.txt
        technical/plos/pmed.0020247.txt:        this burden is often a downward spiral marked by fatalism, self-loathing, and isolation
        technical/plos/pmed.0020247.txt:        the chosen. This theological approach warrants valorizing or stigmatizing people as “saved”
        technical/plos/pmed.0020247.txt:        dynamics and challenge assumptions and warrants of privilege.
        technical/plos/pmed.0020249.txt:          most straight-forward design would involve a large number of hosts, some vaccinated and
        technical/plos/pmed.0020249.txt:        Spearman-Kärber [40] or single-parameter methods [41], and there is software available,
        technical/plos/pmed.0020249.txt:        shift of focus towards indirect effects of vaccine candidates on the pathogenicity of the
        technical/plos/pmed.0020249.txt:        transmission and pathogenesis, and thus would provide further guidance toward an effective
        technical/plos/pmed.0020257.txt:        be on a separate ward, and 40% believed a person's HIV status could be determined by their
        technical/plos/pmed.0020257.txt:        precautions against HIV transmission were more likely to favor restrictive policies towards
        technical/plos/pmed.0020257.txt:        treatment and in ethics were more likely to report negative attitudes towards patients with
        technical/plos/pmed.0020257.txt:        towards patients with HIV/AIDS existed among a significant proportion. Inadequate education
        technical/plos/pmed.0020272.txt:        Too often editors and reviewers reward only the cleanest results and the most
        technical/plos/pmed.0020272.txt:        straightforward conclusions. At
        technical/plos/pmed.0020274.txt:        However, the authors warned that the high percentage of HCoV-NL63-positive samples could
        ```
        - Now there is a problem: even though I want to broaden my search for the keyword "war" in order to ignore case sensitivity, it searches for the pattern of characters, rather than the word. How can we circumvent this issue? 
    
## The 'grep' command: Option -w
- The -w option searches for words, as opposed to patterns of characters. 
    - It is useful for searching for the exact pattern of characters as displayed by words. 
    - Example 1: "war" 
        ```
        [cs15lfa22ks@ieng6-203]:skill-demo1:358$ grep -w "war" */*/*.txt
        technical/911report/chapter-6.txt:            Similarly, Berger recalled that to go to war, a president needs to be able to say
        technical/911report/chapter-6.txt:                order to go to war or deliver an ultimatum to the Taliban threatening war. The
        technical/911report/chapter-6.txt:                decisively in the civil war in order to change Afghanistan's government. By the end
        technical/911report/chapter-6.txt:                Taliban in the civil war and attack al Qaeda bases, while the United States
        technical/911report/chapter-6.txt:                killing Bin Ladin, not for war. Looking back in 2004, he equated the presidential
        technical/911report/chapter-7.txt:                counterproductive. It might draw the Americans into the war against them, just when
        technical/biomed/1472-6882-1-10.txt:          as a charm before going to war [ 103 ] . Another species
        technical/plos/pmed.0010010.txt:        countries now, but what we could accomplish if we joined together to really fight this war
        technical/plos/pmed.0020062.txt:        need to change. In recent years, in order to improve their lives economically or avoid war
        technical/plos/pmed.0020209.txt:            of our soldiers that were killed in the Vietnam war [who] died as a result of Vioxx
        technical/plos/pmed.0020216.txt:        country. By pushing rural residents from war-torn areas to the capital, Kathmandu, the
        ```
        - Here, I have found exact matches for "war" instead of war in "downward" or "towards".
    - Example 2: "earn" 
        ```
        [cs15lfa22ks@ieng6-203]:skill-demo1:369$ grep -w  "earn" */*/*.txt
        technical/plos/journal.pbio.0020147.txt:        engagingly admit that for their project to succeed the new theory must earn its keep by
        technical/plos/pmed.0010056.txt:        about intellectual property rights unless they expect to earn a profit. This explains why
        ```
        - We find exact matches for "earn" instead of earn in "learned" or "learn". We find earn in the context we want to find it in. 
    - Example 3: "Bush"
        ``` 
        [cs15lfa22ks@ieng6-203]:skill-demo1:369$ grep -w -i  "Bush" */*/*.txt
        technical/911report/chapter-8.txt:            He in turn met daily with President Bush, who was briefed by the CIA through what is
        technical/911report/chapter-8.txt:            Reports similar to many of these were made available to President Bush in morning
        technical/911report/chapter-8.txt:                airport during the G-8 summit, which President Bush attended.
        technical/911report/chapter-8.txt:            During the spring and summer of 2001, President Bush had on several occasions asked
        technical/911report/chapter-8.txt:                historical in nature. President Bush said the article told him that al Qaeda was
        technical/911report/chapter-8.txt:                President George W. Bush on August 6, 2001.37 Redacted material is indicated by
        technical/911report/chapter-8.txt:                in the United States. DCI Tenet visited President Bush in Crawford, Texas, on August
        technical/911report/chapter-8.txt:                the summer. In addition to his daily meetings with President Bush, and weekly
        technical/biomed/1471-2091-3-4.txt:        schemes [ 8 9 10 11 12 13 14 15 ] . For example, Bush has
        technical/biomed/1471-2091-3-4.txt:        15 ] . One of the more alarming groups are the Bush group 3
        technical/biomed/1471-2091-3-4.txt:        further divided by Bush into subgroups based on amino acid
        technical/biomed/1472-6882-1-10.txt:          their bush medicine remedies. One research hazard was the
        technical/biomed/1472-6882-1-10.txt:          Nicotiana tabacum ), snake bush (
        technical/biomed/1472-6882-1-10.txt:          bush (
        ```
        - We can combine options in order to present a broader depth to our searches!
            - Perhaps I wanted to find information about both President Bush and the bush. Now I can find what I want in the context in which I expected it to be presented, not as an adjective in a totally different context (perhaps bush was being used to say a bush was bushy).
## The 'grep' command: Option -l
- The -l option only returns the file names which have the specified pattern of characters and does not print out the line in which they appear
    - Useful if you wanted to see if a certain pattern of characters existed in order to index the file in which it existed. 
    - Example 1: "halo" 
        ```
        [cs15lfa22ks@ieng6-203]:skill-demo1:378$ grep -l "halo" */*/*.txt
        technical/biomed/1471-2091-3-4.txt
        technical/biomed/1471-213X-1-6.txt
        technical/biomed/1471-213X-1-9.txt
        technical/biomed/1471-213X-2-1.txt
        technical/biomed/1471-2148-1-14.txt
        technical/biomed/1471-2148-1-8.txt
        technical/biomed/1471-2148-2-7.txt
        technical/biomed/1471-2148-3-18.txt
        technical/biomed/1471-2164-3-33.txt
        technical/biomed/1471-2164-3-4.txt
        technical/biomed/1471-2172-4-2.txt
        technical/biomed/1471-2180-3-5.txt
        ```
        - I only want to see the names of the files which have the pattern of characters "halo" in them to determine the context in which the pattern of character is commonly used. Since they all happen to be in the biomed directory, I can assume that "halo" would have to do with something biological. 
    - Example 2: "German"
        ```
        [cs15lfa22ks@ieng6-203]:skill-demo1:381$ grep -l -w "German" */*/*.txt
        technical/911report/chapter-13.4.txt
        technical/911report/chapter-13.5.txt
        technical/911report/chapter-3.txt
        technical/911report/chapter-5.txt
        technical/911report/chapter-8.txt
        technical/biomed/1471-213X-3-7.txt
        technical/biomed/1471-2458-2-6.txt
        technical/biomed/1472-6920-2-3.txt
        technical/biomed/1472-6947-3-8.txt
        technical/biomed/1472-6963-3-11.txt
        technical/plos/journal.pbio.0020101.txt
        technical/plos/journal.pbio.0020161.txt
        technical/plos/journal.pbio.0020419.txt
        technical/plos/journal.pbio.0020440.txt
        technical/plos/pmed.0020034.txt
        ```
        - I want to see the file names which contain the word "German". It would be helpful in deducing if the German contribution to world affairs and biology is important. 
    - Example 3: "legend"
        ```
        [cs15lfa22ks@ieng6-203]:skill-demo1:382$ grep -l -w "legend" */*/*.txt
        technical/biomed/1471-2091-2-10.txt
        technical/biomed/1471-2105-3-6.txt
        technical/biomed/1471-2121-2-18.txt
        technical/biomed/1471-2148-1-8.txt
        technical/biomed/1471-2202-2-19.txt
        technical/biomed/1471-2210-1-7.txt
        technical/biomed/1471-2229-1-2.txt
        technical/biomed/1471-2229-2-11.txt
        technical/biomed/1471-2334-2-27.txt
        technical/biomed/1472-6793-1-15.txt
        technical/biomed/1472-6793-2-2.txt
        technical/biomed/gb-2001-2-7-research0025.txt
        technical/biomed/gb-2002-3-12-research0080.txt
        technical/biomed/gb-2002-3-5-research0024.txt
        technical/biomed/gb-2002-3-9-research0045.txt
        technical/biomed/gb-2002-3-9-research0051.txt
        ```
        - I want to see if there is anything fun, like a fantasy tale, worth reading in the technical directory and its subdirectories and I find out that there exists none. I am disappointed. 

## The 'grep' command: Option -q
- This makes the grep command print out nothing, exiting immediately if a match is found, even if an error is detected. 
    - Example 1: "middle-aged in the next decade."
        ```
        [cs15lfa22ks@ieng6-203]:skill-demo1:383$ grep -q "middle-aged in the next decade." */*/*.txt
        [cs15lfa22ks@ieng6-203]:skill-demo1:384$ 
        ```
        - This is not particularly useful.
