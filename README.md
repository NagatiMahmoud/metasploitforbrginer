 # metasploit for brginer
 in this toturial i will explit basic metasploit and scan of network commands and how can i get SSH access to main route servers
 by forcing credentials (metasploit or hydra methode) also how can i enumerate MySQL databases with Metasploit
 
Network Scan 1: 
![arch1](https://user-images.githubusercontent.com/81563813/152137110-cba55b6a-e9e1-427a-8139-30e6d99a47b6.PNG)

Conclusion : 

![architect1](https://user-images.githubusercontent.com/81563813/152137227-82472793-a573-401c-a08f-f05212b96b31.png)

Main Road Services Scan:
![scan serv1](https://user-images.githubusercontent.com/81563813/152137317-3bca205e-f044-492a-a1a5-bb8f13a94b8b.PNG)

We choose the ssh service open on port 22 and the tcp protocol to have an ssh connection from the vulnerabilities of this service on the metasploit framework.

Get SSH access to the main route servers by forcing credentials : 
Methode 1 :  Metasploit 
a-start Metasploit :
![startmetasploit](https://user-images.githubusercontent.com/81563813/152137705-b3682874-947f-42e3-ad76-b3f7dd1cba6b.PNG)

b- find the appropriate module with the search command:
![searchssh](https://user-images.githubusercontent.com/81563813/152137905-b111ab6f-634c-48be-83b1-8e8555478589.PNG)
![searchssh2](https://user-images.githubusercontent.com/81563813/152137914-251fba75-7235-48b9-bb2c-23afb67dfed4.PNG)

c- The ssh_login module is exactly what we need. By giving it the use command, we can then type in options to display the parameters available to the parser: 

![usecommande options](https://user-images.githubusercontent.com/81563813/152138428-0c6b3eac-b0de-4cff-9b18-b441a5ad068f.PNG)

We need to define a few things for this to work properly. First, RHOSTS is the IP address of our target. Next, STOP_ON_SUCCESS will stop after finding valid credentials. Next, USER_FILE is a list of user names. And PASS_FILE is a list of passwords. Finally, there is VERBOSE, which will display all attempts.

![set](https://user-images.githubusercontent.com/81563813/152138577-9ee41750-ac7f-45cb-86e7-fe3a3f151947.PNG)

We should be ready now. Type run at the prompt to start it:

![runssh](https://user-images.githubusercontent.com/81563813/152138724-ae1c247b-78c9-4a01-9223-3f17002ebd9c.PNG)

We should be ready now. Type run at the prompt to run it:For the user and password files, I used a short list containing known credentials for the purposes of this demonstration. 

Method 2: Hydra
The next tool we will use is Hydra, a powerful connection cracker that is very fast and supports a number of different protocols. 

![hydra](https://user-images.githubusercontent.com/81563813/152138940-b634120e-0175-48b9-9f3d-5132995a52af.PNG)

now we provide an ssh connection with main route:

![sshconnectio](https://user-images.githubusercontent.com/81563813/152139087-034c65f9-12d8-47ac-9b5f-c89955854522.PNG)


After that we show the route table to know all the machines on the same network with main route.

![routetableofrp](https://user-images.githubusercontent.com/81563813/152139407-47a995f9-3f2f-464d-8b49-2a709a14a665.PNG)

Analysis of the network 192.168.10.0: 

![souresoux2](https://user-images.githubusercontent.com/81563813/152139582-cda9517a-aaba-4263-a3c9-ccd8e47f9202.png)

Conclusion : 
![architect3](https://user-images.githubusercontent.com/81563813/152139652-9db03a45-1983-422a-bce6-978667fd5495.png)

Now, to expect the main route from all the machines in the same network, we need to define the routing table in the kali machine with this command:
 $ route add -net 192.168.10.0 netmask 255.255.255.0 gw 192.168.0.200
 
 Scan of VULN services:
 
![servicevuln](https://user-images.githubusercontent.com/81563813/152139879-d9b0d22a-cf52-4b7f-9a96-2889989af0d9.PNG)

We can choose the ssh service open on port 22 and the tcp protocol to have an ssh connection from the vulnerabilities of this service on the metasploit framework, or we can choose the rpcbind service.

Enumerate MySQL databases with Metasploit :
Step 1: Get login information
Search for all MySQL related modules using the search command:

![myslenum](https://user-images.githubusercontent.com/81563813/152140348-2045e865-4e3a-4998-970b-81fe20f45e59.png)

