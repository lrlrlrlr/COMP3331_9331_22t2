# COMP3331_9331_22t2
For H12A and H14A students.

## General info:
 - [Course outline](https://webcms3.cse.unsw.edu.au/COMP3331/22T2/outline)  

## Assignment design
 - MUST use UDP for P2P part (otherwise you will lose marks).
 - Use 'try...except...' to catch every exception so your client and server will not crash.
 - Follow the SPEC to design your application, your application should have SAME output as the SPEC example.


## Assignment Test Instructions
Note: Please try to run your application with the follwing commands, and check if you have expected output. This is not an official testcase, just for reference, please always follow the instructions of **[Assignment SPEC](https://webcms3.cse.unsw.edu.au/static/uploads/course/COMP3331/22T2/040c4d358872ea23642cddd25ae78bbe77de773a4772d04bf0ea82612014b4c2/Assigment_22T2-version-1.0.pdf)**.

### login
 - login with correct password
 - login with incorrect password, for 3 times. -- the client terminal should shutdown and user should be blocked.
 - login with with a blocked username, from another client(new terminal).
 - login with a username that does not exist
 - Check the page 13~14 in SPEC, make sure you have the same output as the examples.
 - try this new [credentials.txt](https://github.com/lrlrlrlr/COMP3331_9331_22t2/blob/main/credentials.txt)  
 
### ATU
 - login Hans, Yoda. Then use Yoda issue the ATU command -- the server should **exclude** the information of the client,
who sends ATU command to the server.
 - login Yoda only, then issue the ATU cmd, it should prompt "no other active user". Also check the logfile *userlog.txt*, make sure the log file is following the format at page 3 SPEC.

### BCM
 - Use Yoda to issue `BCM  ` command, The client should display an error message.
 - Use Yoda to issue `BCM Hello world! COMP3331` command, then check the logfile *messagelog.txt*, make sure the format is following the page 4 SPEC:
 ```
 messageNumber; timestamp; username; message 
 1; 1 Jun 2022 21:39:04; yoda; Hello world! COMP3331
 ```  
 - Then login Hans, issue the command `RDM b 1 Jun 2022 21:39:00` -- you should be able to see the message from Yoda.
 
### SRB & SRM & RDM
 - Login Yoda only, then issue command `SRB` and `SRB Yoda` and `SRB Hans`, the client should display an error message.
 - Login Yoda and Hans, then issue command `SRB Hans` in yoda's terminal and issue the command `SRB Yoda` in Hans' terminal , you should have 2 room now (id 1 and 2)
 - Following the last one
   - issue `SRM` in Yoda's terminal, the client should display an error message.  
   - issue the command `SRM 1 Hi, Hans` and `SRM 2 Hi, Hans` in Yoda's terminal -- should be succesful.
 - Following the last one, 
   - issue `RDM` in Yoda's terminal, the client should display an error message.
   - issue the command `RDM s 1 Jun 2033 21:39:00` in Hans' terminal -- should have no message been shown since the timestamp is year 2033.
   - issue the command `RDM s 1 Jun 2022 21:39:00` in Hans' terminal -- should be succesful display the Yoda's messages in room 1 and 2.
                           
### OUT
 - Login to Yoda, check the active user log, yoda should be in the logfile. 
 - Issue command `BCM Hello world!`, then issue `OUT`, check the active user log, yoda should not be in the logfile now. Then check messagelog.txt, yoda's message should still inside the file.
 
### P2P
 - Check the code in *client.py*, make sure it is **UDP** instead of **TCP**;
 - Download the video file [ski.mp4](https://github.com/lrlrlrlr/COMP3331_9331_22t2/blob/main/ski.mp4), put it in the same folder with *client.py*.
 - Login to Yoda only, then issue `UPD` and `UPD Hans Filenotexist.mp4` and `UPD Hans ski.mp4`, your client should prompt an error message. 
 - Login to Yoda and Hans, then try to run `UPD Hans ski.mp4` in Yoda's terminal, you should be able to find the *yoda_ski.mp4* in the folder, try to play the video, see if it is playable.

 
