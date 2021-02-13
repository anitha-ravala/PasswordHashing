 # Password Hashing Application


## About the Project

JumpCloud has implemented a password hashing application in Golang. This application supports 3 end points 

  ○ A POST to /hash should accept a password. It should return a job identifier immediately. It should then wait 5 seconds and compute the password hash. 
  
  ○ A GET to /hash should accept a job identifier. It should return the base64 encoded password hash for the corresponding POST request.
  
  ○ A GET to /stats should accept no data. It should return a JSON data structure for the total hash requests since the server started and the average time of a hash request in     milliseconds.
  
This software should be able to process multiple connections simultaneously. The software should support a graceful shutdown request. Meaning, it should allow any
in-flight password hashing to complete, reject any new requests, respond with a Service Unavailable and shutdown.No additional password requests should be allowed when shutdown is pending.

## Built With
  
  ○ SHA152 algorithm


## Getting Started

 ### Prerequisites

1. Set up the PORT to 8088 under Environment Variables
 
2. Download and install 7zip
https://www.7-zip.org/download.html

3. Curl for Windows or Gitbach

### Installation

For Windows

1. Either Click on url : https://s3.amazonaws.com/qa-broken-hashserve/broken-hashserve.tgz 
or
Go to powershell and run the command “iwr -Uri https://s3.amazonaws.com/qa-broken-hashserve/broken-hashserve.tgz -UseBasicParsing -o ./broken-hashserve.tgz”
2. This creates a file “broken-hashserve.tgz”
3. Unzip “broken-hashserve.tgz” file using 7zip. Extract the files and it will creates folder with “broken-hashserve.tar” file 
4. Unzip the broken-hashserve.tar” file and this create a folder with application versions for each OS. For ex: windows have “broken-hashserve_win.exe
5. Run the broken-hashserve_win.exe 
6. Open new CMD window after PORT variable is created

## Usage

You can interact with the application using curl. The following are examples that would/should generate similar returns - the job identifier does not need to conform to a specification.
●  To Post to the /hash endpoint
Use the below commandto POST 
$ curl -X POST -H "Content-Type:application/json" -d "{\"password\":\"angrymonkey\"}" http://127.0.0.1:8088/hash
Application will display the job identifier as 1 for the first job 

● To Get the base64 encoded password
Use the following command
$ curl -H "application/json" http://127.0.0.1:8088/hash/1
Application will display a hash. For example see the below
> zHkbvZDdwYYiDnwtDdv/FIWvcy1sKCb7qi7Nu8Q8Cd/MqjQeyCI0pWKDGp74A1g==
● To Get the stats
Use the below command
$ curl http://127.0.0.1:8088/stats
Application will display TotalRequests along with AverageTime as below in JSON format 
> {"TotalRequests":3,"AverageTime":5004625}
● To Shutdown the application use the below command
curl -X POST -d "shutdown" http://127.0.0.1:8088/hash
Application will shutdown 

 
Contact
Anitha Ravala - email@anitha.ravala@gmail.com

Project Link: https://github.com/your_username/repo_name

