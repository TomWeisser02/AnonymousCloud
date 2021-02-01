--------------- WIP !!! ----------  PLEASE IGNORE FOR NOW 
# 1. AnonymousCloud
This program's goal is to ensure an encrypted connection between client and server and high standards when it comes to data privacy.

# 2. Preface
Hello! Thank you for showing interest for my project I am currently working on. Let me introduce you to myself: I am Tom, 18 y/o, living in germany and I am programming for three years now. This is my first project I've ever published and it won't be the last. It took me around 55 hours (6 days) for everything to learn, plan and develop. During the development, I gained a lot of information about cryptography and all of it's details.
So much about me and the background stuff, let's start with the project!

# 3. What does the Software provide?
AnonymousCloud is written in Python and uses sockets and encryption to provide a secure file transmission between client and server. On top, the server owner can only see, how much space is being used and how the files are structured. Due to encryption with a secret key that only the client posseses and the files being stored with fake names and fake extensions, the server owner has no chance to get insight of what the users are storing. In other words: The server provides space on which data can be stored without the user having to be afraid of leaking any data to the server owner or to a potential hacker attacking the server. 
The project contains three .py script files, which are the client, the server and the remote file explorer(which was the hardest to develop). To get a deeper understanding about how the software works, I want to explain every Python script file one by one.

# 3.1 Server.py
The server can handle many users at the time (how many can be assigned in the settings) and controlls access with a login system. When connecting, the server creates a       Client-object, which gets stored in a list, where all currently active users are stored and starts a thread which handles the user. I've also planned to implement a process mode, which allocates every user to a new process. This is to seperate client handling from server activity even more pronounced. When the client-server connection has been established, the encryption key, to cipher all in- and outcoming traffic between both parties, has to be generated. This is done by the client, which has to somehow deliver the key savely. For this matter, the server has a public-key, which also gets generated with every boot and sends it to the client, so that the symmetric key can be encrypted and send to the server. In other words, I used a simple key encapsulation algorithm and soon it will be replaced with the Diffie-Hellman algorithm, which is basically a more advanced version. 
When everything worked fine, all messages will be encrypted for now on with the secret key and the user has now to decide, whether to register or to login with an already existing account. All accounts are store in a SQL-database in which user ID, username, password and the name of virtual harddrive is being stored. When signing or loggin in, the user password runs through a SHA256 hashing algorithm (which is provided by a python lib) and is send over to the server to compare both hashes. Since this is a fresh new project, protections against bruteforce attacks or bad user inputs (like bad passwords, names, etc.) are missing and will be implemented. 
Now that the user is logged in, the client can either send or receive their files. Whenever the server receives commands from the client, the server always returns a response if everything worked fine and to keep both processes synchronized. So when the user asks to send files, it gets a "success" or a "fail". When succeeding, the server then receives the file and buffer size, after the user selected which file on his pc to send over. The buffer size is a integer which determines the amount of bytes a packet contains. After the user selected the location in the virtual space, the file transmission now begins. The file transmission and location selection needs an entire chapter, so we save this for later.

# FUTURE PLANS
- Encrypted chat
- Encrypted voice chat
- Encrypted video chat
