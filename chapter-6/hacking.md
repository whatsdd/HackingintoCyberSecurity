# Hacking

### **Hacking** <a href="#_61gtujtdzc0f" id="_61gtujtdzc0f"></a>

### Programming <a href="#_7vwzvdhotzp0" id="_7vwzvdhotzp0"></a>

Hacker is a term for both those who write code and those who exploit it. Even though these two groups of hackers have different end goals, both groups use similar problem-solving techniques. Since an understanding of programming helps those who exploit, and an understanding of exploitation helps those who program, many hackers do both. There are interesting hacks found in both the techniques used to write elegant code and the techniques used to exploit programs. Hacking is really just the act of finding a clever and counterintuitive solution to a problem.

The hacks found in program exploits usually use the rules of the computer to bypass security in ways never intended. Programming hacks are similar in that they also use the rules of the computer in new and inventive ways, but the final goal is efficiency or smaller source code, not necessarily a security compromise. There are actually an infinite number of programs that can be written to accomplish any given task, but most of these solutions are unnecessarily large, complex, and sloppy. The few solutions that remain are small, efficient, and neat. Programs that have these qualities are said to have elegance, and the clever and inventive solutions that tend to lead to this efficiency are called hacks. Hackers on both sides of programming appreciate both the beauty of elegant code and the ingenuity of clever hacks.

In the business world, more importance is placed on churning out functional code than on achieving clever hacks and elegance. Because of the tremendous exponential growth of computational power and memory, spending an extra five hours to create a slightly faster and more memory efficient piece of code just doesn’t make business sense when dealing with modern computers that have gigahertz of processing cycles and gigabytes of memory. While time and memory optimizations go without notice by all but the most sophisticated of users, a new feature is marketable. When the bottom line is money, spending time on clever hacks for optimization just doesn’t make sense.

True appreciation of programming elegance is left for the hackers: computer hobbyists whose end goal isn’t to make a profit but to squeeze every possible bit of functionality out of their old Commodore 64s, exploit writers who need to write tiny and amazing pieces of code to slip through narrow security cracks, and anyone else who appreciates the pursuit and the challenge of finding the best possible solution. These are the people who get excited about programming and really appreciate the beauty of an elegant piece of code or the ingenuity of a clever hack. Since an understanding of programming is a prerequisite to understanding how programs can be exploited, programming is a natural starting point.

**What Is Programming?**

Programming is a very natural and intuitive concept. A program is nothing more than a series of statements written in a specific language. Programs are everywhere, and even the technophobes of the world use programs every day. Driving directions, cooking recipes, football plays, and DNA are all types of programs.

Anyone who knows English can understand and follow these driving directions, since they’re written in English. Granted, they’re not eloquent, but each instruction is clear and easy to understand, at least for someone who reads English.

But a computer doesn’t natively understand English; it only understands machine language. To instruct a computer to do something, the instructions must be written in its language. However, machine language is arcane and difficult to work with—it consists of raw bits and bytes, and it differs from architecture to architecture. To write a program in machine language for an Intel x86 processor, you would have to figure out the value associated with each instruction, how each instruction interacts, and myriad low-level details. Programming like this is painstaking and cumbersome, and it is certainly not intuitive. What’s needed to overcome the complication of writing machine language is a translator. An assembler is one form of machine-language translator—it is a program that translates assembly language into machine-readable code. Assembly language is less cryptic than machine language, since it uses names for the different instructions and variables, instead of just using numbers. However, assembly language is still far from intuitive. The instruction names are very esoteric, and the language is architecture specific. Just as machine language for Intel x86 processors is different from machine language for Sparc processors, x86 assembly language is different from Sparc assembly language. Any program written using assembly language for one processor’s architecture will not work on another processor’s architecture. If a program is written in x86 assembly language, it must be rewritten to run on Sparc architecture. In addition, in order to write an effective program in assembly language, you must still know many low-level details of the processor architecture you are writing for.

These problems can be mitigated by yet another form of translator called a compiler. A compiler converts a high-level language into machine language. High-level languages are much more intuitive than assembly language and can be converted into many different types of machine language for different processor architectures. This means that if a program is written in a high level language, the program only needs to be written once; the same piece of program code can be compiled into machine language for various specific architectures. C, C++, and Fortran are all examples of high-level languages. A program written in a high-level language is much more readable and English-like than assembly language or machine language, but it still must follow very strict rules about how the instructions are worded, or the compiler won’t be able to understand it.

**Pseudo-code**

Programmers have yet another form of programming language called pseudo-code. Pseudo-code is simply English arranged with a general structure similar to a high-level language. It isn’t understood by compilers, assemblers, or any computers, but it is a useful way for a programmer to arrange instructions. Pseudo-code isn’t well defined; in fact, most people write pseudo-code slightly differently. It’s sort of the nebulous missing link between English and high-level programming languages like C. Pseudo-code makes for an excellent introduction to common universal programming concepts.

**Control Structures**

Without control structures, a program would just be a series of instructions executed in sequential order. This is fine for very simple programs, but most programs, like the driving directions example, aren’t that simple. The driving directions included statements like, Continue on Main Street until you see a church on your right and If the street is blocked because of construction. These statements are known as control structures, and they change the flow of the program’s execution from a simple sequential order to a more complex and more useful flow.

**If-Then-Else**

In the case of our driving directions, Main Street could be under construction. If it is, a special set of instructions needs to address that situation. Otherwise, the original set of instructions should be followed. These types of special cases can be accounted for in a program with one of the most natural control structures: the if-then-else structure.

**While/Until Loops**

Another elementary programming concept is the while control structure, which is a type of loop. A programmer will often want to execute a set of instructions more than once. A program can accomplish this task through looping, but it requires a set of conditions that tells it when to stop looping, lest it continue into infinity. A while loop says to execute the following set of instructions in a loop while a condition is true.

**For Loops**

Another looping control structure is the for loop. This is generally used when a programmer wants to loop for a certain number of iterations. The driving direction Drive straight down Destination Road for 5 miles could be converted to a for loop.

### Exploitation <a href="#_gzp4iagl9z4i" id="_gzp4iagl9z4i"></a>

Program exploitation is a staple of hacking. As demonstrated in the previous chapter, a program is made up of a complex set of rules following a certain execution flow that ultimately tells the computer what to do. Exploiting a program is simply a clever way of getting the computer to do what you want it to do, even if the currently running program was designed to prevent that action. Since a program can really only do what it’s designed to do, the security holes are actually flaws or oversights in the design of the program or the environment the program is running in. It takes a creative mind to find these holes and to write programs that compensate for them. Sometimes these holes are the products of relatively obvious programmer errors, but there are some less obvious errors that have given birth to more complex exploit techniques that can be applied in many different places.

A program can only do what it’s programmed to do, to the letter of the law. Unfortunately, what’s written doesn’t always coincide with what the programmer intended the program to do. This principle can be explained with a joke:

_A man is walking through the woods, and he finds a magic lamp on the ground. Instinctively, he picks the lamp up, rubs the side of it with his sleeve, and out pops a genie. The genie thanks the man for freeing him, and offers to grant him three wishes. The man is ecstatic and knows exactly what he wants._

_“First,” says the man, “I want a billion dollars.”_

_The genie snaps his fingers and a briefcase full of money materializes out of thin air._

_The man is wide eyed in amazement and continues, “Next, I want a Ferrari.”_

_The genie snaps his fingers and a Ferrari appears from a puff of smoke._

_The man continues, “Finally, I want to be irresistible to women.”_

_The genie snaps his fingers and the man turns into a box of chocolates._

Just as the man’s final wish was granted based on what he said, rather than what he was thinking, a program will follow its instructions exactly, and the results aren’t always what the programmer intended. Sometimes the repercussions can be catastrophic.

Programmers are human, and sometimes what they write isn’t exactly what they mean. For example, one common programming error is called an off-by-one error. As the name implies, it’s an error where the programmer has miscounted by one. This happens more often than you might think, and it is best illustrated with a question: If you’re building a 100-foot fence, with fence posts spaced 10 feet apart, how many fence posts do you need? The obvious answer is 10 fence posts, but this is incorrect, since you actually need 11. This type of off-by-one error is commonly called a fencepost error, and it occurs when a programmer mistakenly counts items instead of spaces between items, or vice versa. Another example is when a programmer is trying to select a range of numbers or items for processing, such as items N through M. If N = 5 and M = 17, how many items are there to process? The obvious answer is M - N, or 17 - 5 = 12 items. But this is incorrect, since there are actually M - N + 1 items, for a total of 13 items. This may seem counterintuitive at first glance, because it is, and that’s exactly why these errors happen.

**Generalized Exploit Techniques**

Off-by-one errors and improper Unicode expansion are all mistakes that can be hard to see at the time but are glaringly obvious to any programmer in hindsight. However, there are some common mistakes that can be exploited in ways that aren’t so obvious. The impact of these mistakes on security isn’t always apparent, and these security problems are found in code everywhere. Because the same type of mistake is made in many different places, generalized exploit techniques have evolved to take advantage of these mistakes, and they can be used in a variety of situations.

Most program exploits have to do with memory corruption. These include common exploit techniques like buffer overflows as well as less-common methods like format string exploits. With these techniques, the ultimate goal is to take control of the target program’s execution flow by tricking it into running a piece of malicious code that has been smuggled into memory. This type of process hijacking is known as execution of arbitrary code, since the hacker can cause a program to do pretty much anything he or she wants it to. Like the LaMacchia Loophole, these types of vulnerabilities exist because there are specific unexpected cases that the program can’t handle. Under normal conditions, these unexpected cases cause the program to crash— metaphorically driving the execution flow off a cliff. But if the environment is carefully controlled, the execution flow can be controlled—preventing the crash and reprogramming the process.

**Buffer Overflows**

Buffer overflow vulnerabilities have been around since the early days of computers and still exist today. Most Internet worms use buffer overflow vulnerabilities to propagate, and even the most recent zero-day VML vulnerability in Internet Explorer is due to a buffer overflow. C is a high-level programming language, but it assumes that the programmer is responsible for data integrity. If this responsibility were shifted over to the compiler, the resulting binaries would be significantly slower, due to integrity checks on every variable. Also, this would remove a significant level of control from the programmer and complicate the language.

While C’s simplicity increases the programmer’s control and the efficiency of the resulting programs, it can also result in programs that are vulnerable to buffer overflows and memory leaks if the programmer isn’t careful. This means that once a variable is allocated memory, there are no built-in safeguards to ensure that the contents of a variable fit into the allocated memory space. If a programmer wants to put ten bytes of data into a buffer that had only been allocated eight bytes of space, that type of action is allowed, even though it will most likely cause the program to crash. This is known as a buffer overrun or buffer overflow, since the extra two bytes of data will overflow and spill out of the allocated memory, overwriting whatever happens to come next. If a critical piece of data is overwritten, the program will crash. The overflow\_example.c code offers an example.

### Networking <a href="#_in8wisdkhmnl" id="_in8wisdkhmnl"></a>

Communication and language have greatly enhanced the abilities of the human race. By using a common language, humans are able to transfer knowledge, coordinate actions, and share experiences. Similarly, programs can become much more powerful when they have the ability to communicate with other programs via a network. The real utility of a web browser isn’t in the program itself, but in its ability to communicate with web servers. Networking is so prevalent that it is sometimes taken for granted. Many applications such as email, the Web, and instant messaging rely on networking. Each of these applications relies on a particular network protocol, but each protocol uses the same general network transport methods. Many people don’t realize that there are vulnerabilities in the networking protocols themselves. In this chapter you will learn how to network your applications using sockets and how to deal with common network vulnerabilities.

**OSI Model**

When two computers talk to each other, they need to speak the same language. The structure of this language is described in layers by the OSI model. The OSI model provides standards that allow hardware, such as routers and firewalls, to focus on one particular aspect of communication that applies to them and ignore others. The OSI model is broken down into conceptual layers of communication. This way, routing and firewall hardware can focus on passing data at the lower layers, ignoring the higher layers of data encapsulation used by running applications. The seven OSI layers are as follows:

**Physical layer** This layer deals with the physical connection between two points. This is the lowest layer, whose primary role is communicating raw bit streams. This layer is also responsible for activating, maintaining, and deactivating these bit-stream communications.

**Data-link layer** This layer deals with actually transferring data between two points. In contrast with the physical layer, which takes care of sending the raw bits, this layer provides high-level functions, such as error correction and flow control. This layer also provides procedures for activating, maintaining, and deactivating data-link connections.

**Network layer** This layer works as a middle ground; its primary role is to pass information between the lower and the higher layers. It provides addressing and routing.

**Transport layer** This layer provides tr

ansparent transfer of data between systems. By providing reliable data communication, this layer allows the higher layers to never worry about reliability or cost-effectiveness of data transmission.

**Session layer** This layer is responsible for establishing and maintaining connections between network applications.

**Presentation layer** This layer is responsible for presenting the data to applications in a syntax or language they understand. This allows for things like encryption and data compression.

**Application layer** This layer is concerned with keeping track of the requirements of the application.

When data is communicated through these protocol layers, it’s sent in small pieces called packets. Each packet contains implementations of these protocol layers. Starting from the application layer, the packet wraps the presentation layer around that data, which wraps the session layer, which wraps the transport layer, and so forth. This process is called encapsulation. Each wrapped layer contains a header and a body. The header contains the protocol information needed for that layer, while the body contains the data for that layer. The body of one layer contains the entire package of previously encapsulated layers, like the skin of an onion or the functional contexts found on a program’s stack.

For example, whenever you browse the Web, the Ethernet cable and card make up the physical layer, taking care of the transmission of raw bits from one end of the cable to the other. The next layer is the data link layer. In the web browser example, Ethernet makes up this layer, which provides the low-level communications between Ethernet ports on the LAN. This protocol allows for communication between Ethernet ports, but these ports don’t yet have IP addresses. The concept of IP addresses doesn’t exist until the next layer, the network layer. In addition to addressing, this layer is responsible for moving data from one address to another. These three lower layers together are able to send packets of data from one IP address to another. The next layer is the transport layer, which for web traffic is TCP; it provides a seamless bidirectional socket connection. The term TCP/IP describes the use of TCP on the transport layer and IP on the network layer. Other addressing schemes exist at this layer; however, your web traffic probably uses IP version 4 (IPv4). IPv4 addresses follow a familiar form of XX.XX.XX.XX. IP version 6 (IPv6) also exists on this layer, with a totally different addressing scheme. Since IPv4 is most common, IP will always refer to IPv4 in this book.

The web traffic itself uses HTTP (Hypertext Transfer Protocol) to communicate, which is in the top layer of the OSI model. When you browse the Web, the web browser on your network is communicating across the Internet with the web server located on a different private network. When this happens, the data packets are encapsulated down to the physical layer where they are passed to a router. Since the router isn’t concerned with what’s actually in the packets, it only needs to implement protocols up to the network layer. The router sends the packets out to the Internet, where they reach the other network’s router. This router then encapsulates this packet with the lower layer protocol headers needed for the packet to reach its final destination. This process is shown in the following illustration.

![](<../.gitbook/assets/0 (5)>)

All of this packet encapsulation makes up a complex language that hosts on the Internet (and other types of networks) use to communicate with each other. These protocols are programmed into routers, firewalls, and your computer’s operating system so they can communicate. Programs that use networking, such as web browsers and email clients, need to interface with the operating system which handles the network communications. Since the operating system takes care of the details of network encapsulation, writing network programs is just a matter of using the network interface of the OS.

**Sockets**

A socket is a standard way to perform network communication through the OS. A socket can be thought of as an endpoint to a connection, like a socket on an operator’s switchboard. But these sockets are just a programmer’s abstraction that takes care of all the nitty-gritty details of the OSI model described above. To the programmer, a socket can be used to send or receive data over a network. This data is transmitted at the session layer (5), above the lower layers (handled by the operating system), which take care of routing. There are several different types of sockets that determine the structure of the transport layer (4). The most common types are stream sockets and datagram sockets.

Stream sockets provide reliable two-way communication similar to when you call someone on the phone. One side initiates the connection to the other, and after the connection is established, either side can communicate to the other. In addition, there is immediate confirmation that what you said actually reached its destination. Stream sockets use a standard communication protocol called Transmission Control Protocol (TCP), which exists on the transport layer (4) of the OSI model. On computer networks, data is usually transmitted in chunks called packets. TCP is designed so that the packets of data will arrive without errors and in sequence, like words arriving at the other end in the order they were spoken when you are talking on the telephone. Web Servers, mail servers, and their respective client applications all use TCP and stream sockets to communicate.

Another common type of socket is a datagram socket. Communicating with a datagram socket is more like mailing a letter than making a phone call. The connection is one-way only and unreliable. If you mail several letters, you can’t be sure that they arrived in the same order, or even that they reached their destination at all. The postal service is pretty reliable; the Internet, however, is not. Datagram sockets use another standard protocol called UDP instead of TCP on the transport layer (4). UDP stands for User Datagram Protocol, implying that it can be used to create custom protocols. This protocol is very basic and lightweight, with few safeguards built into it. It’s not a real connection, just a basic method for sending data from one point to another. With datagram sockets, there is very little overhead in the protocol, but the protocol doesn’t do much. If your program needs to confirm that a packet was received by the other side, the other side must be coded to send back an acknowledgment packet. In some cases packet loss is acceptable.

Datagram sockets and UDP are commonly used in networked games and streaming media, since developers can tailor their communications exactly as needed without the built-in overhead of TCP.

**Socket Functions**

In C, sockets behave a lot like files since they use file descriptors to identify themselves. Sockets behave so much like files that you can actually use the read() and write() functions to receive and send data using socket file descriptors. However, there are several functions specifically designed for dealing with sockets. These functions have their prototypes defined in /usr/include/ sys/sockets.h.

_**socket(int domain, int type, int protocol)**_

Used to create a new socket, returns a file descriptor for the socket or -1 on error.

_**connect(int fd, struct sockaddr \*remote\_host, socklen\_t addr\_length)**_

Connects a socket (described by file descriptor fd) to a remote host. Returns 0 on success and -1 on error.

_**bind(int fd, struct sockaddr \*local\_addr, socklen\_t addr\_length)**_

Binds a socket to a local address so it can listen for incoming connections. Returns 0 on success and -1 on error.

_**listen(int fd, int backlog\_queue\_size)**_

Listens for incoming connections and queues connection requests up to backlog\_queue\_size. Returns 0 on success and -1 on error.

_**accept(int fd, sockaddr \*remote\_host, socklen\_t \*addr\_length)**_

Accepts an incoming connection on a bound socket. The address information from the remote host is written into the remote\_host structure and the actual size of the address structure is written into \*addr\_length. This function returns a new socket file descriptor to identify the connected socket or -1 on error.

**send(int fd, void \*buffer, size\_t n, int flags)**

Sends n bytes from \*buffer to socket fd; returns the number of bytes sent or -1 on error.

**recv(int fd, void \*buffer, size\_t n, int flags)**

Receives n bytes from socket fd into \*buffer; returns the number of bytes received or -1 on error.

When a socket is created with the socket() function, the domain, type, and protocol of the socket must be specified. The domain refers to the protocol family of the socket. A socket can be used to communicate using a variety of protocols, from the standard Internet protocol used when you browse the Web to amateur radio protocols such as AX.25 (when you are being a gigantic nerd). These protocol families are defined in bits/socket.h, which is automatically included from sys/socket.h.

### Shellcode <a href="#_k41aldojn210" id="_k41aldojn210"></a>

So far, the shellcode used in our exploits has been just a string of copied and pasted bytes. We have seen standard shell-spawning shellcode for local exploits and port-binding shellcode for remote ones. Shellcode is also sometimes referred to as an exploit payload, since these self-contained programs do the real work once a program has been hacked. Shellcode usually spawns a shell, as that is an elegant way to hand off control; but it can do anything a program can do. Unfortunately, for many hackers the shellcode story stops at copying and pasting bytes. These hackers are just scratching the surface of what’s possible. Custom shellcode gives you absolute control over the exploited program. Perhaps you want your shellcode to add an admin account to /etc/passwd or to automatically remove lines from log files. Once you know how to write your own shellcode, your exploits are limited only by your imagination. In addition, writing shellcode develops assembly language skills and employs a number of hacking techniques worth knowing.

**Assembly vs. C**

The shellcode bytes are actually architecture-specific machine instructions, so shellcode is written using the assembly language. Writing a program in assembly is different from writing it in C, but many of the principles are similar. The operating system manages things like input, output, process control, file access, and network communication in the kernel. Compiled C programs ultimately perform these tasks by making system calls to the kernel. Different operating systems have different sets of system calls.

In C, standard libraries are used for convenience and portability. A C program that uses printf() to output a string can be compiled for many different systems, since the library knows the appropriate system calls for various architectures. A C program compiled on an x86 processor will produce x86 assembly language.

By definition, assembly language is already specific to a certain processor architecture, so portability is impossible. There are no standard libraries; instead, kernel system calls have to be made directly. To begin our comparison, let’s write a simple C program, then rewrite it in x86 assembly.

When the compiled program is run, execution flows through the standard I/O library, eventually making a system call to write the string Hello, world! to the screen. The strace program is used to trace a program’s system calls. Used on the compiled helloworld program, it shows every system call that program makes.

The compiled program does more than just print a string. The system calls at the start are setting up the environment and memory for the program, but the important part is the write() syscall shown in bold. This is what actually outputs the string.

The strace output also shows the arguments for the syscall. The buf and count arguments are a pointer to our string and its length. The fd argument of 1 is a special standard file descriptor. File descriptors are used for almost everything in Unix: input, output, file access, network sockets, and so on. A file descriptor is similar to a number given out at a coat check. Opening a file descriptor is like checking in your coat, since you are given a number that can later be used to reference your coat. The first three file descriptor numbers (0, 1, and 2) are automatically used for standard input, output, and error. These values are standard and have been defined in several places, such as the /usr/include/unistd.h file on the following page.

**The Path to Shellcode**

Shellcode is literally injected into a running program, where it takes over like a biological virus inside a cell. Since shellcode isn’t really an executable program, we don’t have the luxury of declaring the layout of data in memory or even using other memory segments. Our instructions must be self-contained and ready to take over control of the processor regardless of its current state. This is commonly referred to as position-independent code.

In shellcode, the bytes for the string "Hello, world!" must be mixed together with the bytes for the assembly instructions, since there aren’t definable or predictable memory segments. This is fine as long as EIP doesn’t try to interpret the string as instructions. However, to access the string as data we need a pointer to it. When the shellcode gets executed, it could be anywhere in memory. The string’s absolute memory address needs to be calculated relative to EIP. Since EIP cannot be accessed from assembly instructions, however, we need to use some sort of trick.

**Assembly Instructions Using the Stack**

The stack is so integral to the x86 architecture that there are special instructions for its operations.

Stack-based exploits are made possible by the call and ret instructions. When a function is called, the return address of the next instruction is pushed to the stack, beginning the stack frame. After the function is finished, the ret instruction pops the return address from the stack and jumps EIP back there. By overwriting the stored return address on the stack before the ret instruction, we can take control of a program’s execution. This architecture can be misused in another way to solve the problem of addressing the inline string data. If the string is placed directly after a call instruction, the address of the string will get pushed to the stack as the return address. Instead of calling a function, we can jump past the string to a pop instruction that will take the address off the stack and into a register. The following assembly instructions demonstrate this technique.

The call instruction jumps execution down below the string. This also pushes the address of the next instruction to the stack, the next instruction in our case being the beginning of the string. The return address can immediately be popped from the stack into the appropriate register. Without using any memory segments, these raw instructions, injected into an existing process, will execute in a completely position-independent way. This means that, when these instructions are assembled, they cannot be linked into an executable.

The nasm assembler converts assembly language into machine code and a corresponding tool called ndisasm converts machine code into assembly. These tools are used above to show the relationship between the machine code bytes and the assembly instructions. The disassembly instructions marked in bold are the bytes of the "Hello, world!" string interpreted as instructions. Now, if we can inject this shellcode into a program and redirect EIP, the program will print out Hello, world! Let’s use the familiar exploit target of the notesearch program.

**Investigating with GDB**

Since the notesearch program runs as root, we can’t debug it as a normal user. However, we also can’t just attach to a running copy of it, because it exits too quickly. Another way to debug programs is with core dumps. From a root prompt, the OS can be told to dump memory when the program crashes by using the command ulimit -c unlimited. This means that dumped core files are allowed to get as big as needed. Now, when the program crashes, the memory will be dumped to disk as a core file, which can be examined using GDB.

Once GDB is loaded, the disassembly style is switched to Intel. Since we are running GDB as root, the .gdbinit file won’t be used. The memory where the shellcode should be is examined. The instructions look incorrect, but it seems like the first incorrect call instruction is what caused the crash. At least, execution was redirected, but something went wrong with the shellcode bytes. Normally, strings are terminated by a null byte, but here, the shell was kind enough to remove these null bytes for us. This, however, totally destroys the meaning of the machine code. Often, shellcode will be injected into a process as a string, using functions like strcpy(). Such functions will simply terminate at the first null byte, producing incomplete and unusable shellcode in memory. In order for the shellcode to survive transit, it must be redesigned so it doesn’t contain any null bytes.

**Shell-Spawning Shellcode**

Now that you’ve learned how to make system calls and avoid null bytes, all sorts of shellcodes can be constructed. To spawn a shell, we just need to make a system call to execute the /bin/sh shell program. System call number 11, execve(), is similar to the C execute() function that we used in the previous chapters.

The first argument of the filename should be a pointer to the string "/bin/sh", since this is what we want to execute. The environment array— the third argument—can be empty, but it still needs to be terminated with a 32-bit null pointer. The argument array—the second argument—must be null terminated, too; it must also contain the string pointer (since the zeroth argument is the name of the running program).

### Countermeasures <a href="#_26spmsa72p79" id="_26spmsa72p79"></a>

The golden poison dart frog secretes an extremely toxic poison—one frog can emit enough to kill 10 adult humans. The only reason these frogs have such an amazingly powerful defense is that a certain species of snake kept eating them and developing a resistance. In response, the frogs kept evolving stronger and stronger poisons as a defense. One result of this coevolution is that the frogs are safe against all other predators. This type of co-evolution also happens with hackers. Their exploit techniques have been around for years, so it’s only natural that defensive countermeasures would develop. In response, hackers find ways to bypass and subvert these defenses, and then new defense techniques are created.

This cycle of innovation is actually quite beneficial. Even though viruses and worms can cause quite a bit of trouble and costly interruptions for businesses, they force a response, which fixes the problem. Worms replicate by exploiting existing vulnerabilities in flawed software. Often these flaws are undiscovered for years, but relatively benign worms such as CodeRed or Sasser force these problems to be fixed. As with chickenpox, it’s better to suffer a minor outbreak early instead of years later when it can cause real damage. If it weren’t for Internet worms making a public spectacle of these security flaws, they might remain unpatched, leaving us vulnerable to an attack from someone with more malicious goals than just replication. In this way, worms and viruses can actually strengthen security in the long run. However, there are more proactive ways to strengthen security. Defensive countermeasures exist which try to nullify the effect of an attack, or prevent the attack from happening. A countermeasure is a fairly abstract concept; this could be a security product, a set of policies, a program, or simply just an attentive system administrator. These defensive countermeasures can be separated into two groups: those that try to detect the attack and those that try to protect the vulnerability.

**Countermeasures That Detect**

The first group of countermeasures tries to detect the intrusion and respond in some way. The detection process could be anything from an administrator reading logs to a program sniffing the network. The response might include killing the connection or process automatically, or just the administrator scrutinizing everything from the machine’s console.

As a system administrator, the exploits you know about aren’t nearly as dangerous as the ones you don’t. The sooner an intrusion is detected, the sooner it can be dealt with and the more likely it can be contained. Intrusions that aren’t discovered for months can be cause for concern.

As a system administrator, the exploits you know about aren’t nearly as dangerous as the ones you don’t. The sooner an intrusion is detected, the sooner it can be dealt with and the more likely it can be contained. Intrusions that aren’t discovered for months can be cause for concern.The way to detect an intrusion is to anticipate what the attacking hacker is going to do. If you know that, then you know what to look for. Countermeasures that detect can look for these attack patterns in log files, network packets, or even program memory. After an intrusion is detected, the hacker can be expunged from the system, any file system damage can be undone by restoring from backup, and the exploited vulnerability can be identified and patched. Detecting countermeasures are quite powerful in an electronic world with backup and restore capabilities.

For the attacker, this means detection can counteract everything he does. Since the detection might not always be immediate, there are a few “smash and grab” scenarios where it doesn’t matter; however, even then it’s better not to leave tracks. Stealth is one of the hacker’s most valuable assets. Exploiting a vulnerable program to get a root shell means you can do whatever you want on that system, but avoiding detection additionally means no one knows you’re there. The combination of “God mode” and invisibility makes for a dangerous hacker. From a concealed position, passwords and data can be quietly sniffed from the network, programs can be backdoored, and further attacks can be launched on other hosts. To stay hidden, you simply need to anticipate the detection methods that might be used. If you know what they are looking for, you can avoid certain exploit patterns or mimic valid ones. The co-evolutionary cycle between hiding and detecting is fueled by thinking of the things the other side hasn’t thought of.

**System Daemons**

To have a realistic discussion of exploit countermeasures and bypass methods, we first need a realistic exploitation target. A remote target will be a server program that accepts incoming connections. In Unix, these programs are usually system daemons. A daemon is a program that runs in the background and detaches from the controlling terminal in a certain way. The term daemon was first coined by MIT hackers in the 1960s. It refers to a molecule-sorting demon from an 1867 thought experiment by a physicist named James Maxwell. In the thought experiment, Maxwell’s demon is a being with the supernatural ability to effortlessly perform difficult tasks, apparently violating the second law of thermodynamics. Similarly, in Linux, system daemons tirelessly perform tasks such as providing SSH service and keeping system logs. Daemon programs typically end with a d to signify they are daemons, such as sshd or syslogd.

With a few additions, the tinyweb.c code on page 214 can be made into a more realistic system daemon. This new code uses a call to the daemon() function, which will spawn a new background process. This function is used by many system daemon processes in Linux, and its man page is shown below.

System daemons run detached from a controlling terminal, so the new tinyweb daemon code writes to a log file. Without a controlling terminal, system daemons are typically controlled with signals. The new tinyweb daemon program will need to catch the terminate signal so it can exit cleanly when killed.

**Crash Course in Signals**

Signals provide a method of interprocess communication in Unix. When a process receives a signal, its flow of execution is interrupted by the operating system to call a signal handler. Signals are identified by a number, and each one has a default signal handler. For example, when CTRL-C is typed in a program’s controlling terminal, an interrupt signal is sent, which has a default signal handler that exits the program. This allows the program to be interrupted, even if it is stuck in an infinite loop. Custom signal handlers can be registered using the signal() function. In the example code below, several signal handlers are registered for certain signals, whereas the main code contains an infinite loop.

**Tinyweb Daemon**

This newer version of the tinyweb program is a system daemon that runs in the background without a controlling terminal. It writes its output to a log file with timestamps, and it listens for the terminate (SIGTERM) signal so it can shut down cleanly when it’s killed.

These additions are fairly minor, but they provide a much more realistic exploit target. The new portions of the code are shown in bold in the listing below.

This daemon program forks into the background, writes to a log file with timestamps, and cleanly exits when it is killed. The log file descriptor and connection-receiving socket are declared as globals so they can be closed cleanly by the handle\_shutdown() function. This function is set up as the callback handler for the terminate and interrupt signals, which allows the program to exit gracefully when it’s killed with the kill command.

The output below shows the program compiled, executed, and killed. Notice that the log file contains timestamps as well as the shutdown message when the program catches the terminate signal and calls handle\_shutdown() to exit gracefully.

This tinywebd program serves HTTP content just like the original tinyweb program, but it behaves as a system daemon, detaching from the controlling terminal and writing to a log file. Both programs are vulnerable to the same overflow exploit; however, the exploitation is only the beginning. Using the new tinyweb daemon as a more realistic exploit target, you will learn how to avoid detection after the intrusion.

### Cryptology <a href="#_n8s9u6302h7d" id="_n8s9u6302h7d"></a>

**(** [Hacking: The Art of Exploitation, 2nd Edition](https://repo.zenk-security.com/Magazine%20E-book/Hacking-%20The%20Art%20of%20Exploitation%20\(2nd%20ed.%202008\)%20-%20Erickson.pdf) **)**

Cryptology is defined as the study of cryptography or cryptanalysis. Cryptography is simply the process of communicating secretly through the use of ciphers, and cryptanalysis is the process of cracking or deciphering such secret communications. Historically, cryptology has been of particular interest during wars, when countries used secret codes to communicate with their troops while also trying to break the enemy’s codes to infiltrate their communications.

The wartime applications still exist, but the use of cryptography in civilian life is becoming increasingly popular as more critical transactions occur over the Internet. Network sniffing is so common that the paranoid assumption that someone is always sniffing network traffic might not be so paranoid. Passwords, credit card numbers, and other proprietary information can all be sniffed and stolen over unencrypted protocols. Encrypted communication protocols provide a solution to this lack of privacy and allow the Internet economy to function. Without Secure Sockets Layer (SSL) encryption, credit card transactions at popular websites would be either very inconvenient or insecure.

All of this private data is protected by cryptographic algorithms that are probably secure. Currently, cryptosystems that can be proven to be secure are far too unwieldy for practical use. So in lieu of a mathematical proof of security, cryptosystems that are practically secure are used. This means that it’s possible that shortcuts for defeating these ciphers exist, but no one’s been able to actualize them yet. Of course, there are also cryptosystems that aren’t secure at all. This could be due to the implementation, key size, or simply cryptanalytic weaknesses in the cipher itself. In 1997, under US law, the maximum allowable key size for encryption in exported software was 40 bits. This limit on key size makes the corresponding cipher insecure, as was shown by RSA Data Security and Ian Goldberg, a graduate student from the University of California, Berkeley. RSA posted a challenge to decipher a message encrypted with a 40-bit key, and three and a half hours later, Ian had done just that. This was strong evidence that 40-bit keys aren’t large enough for a secure cryptosystem.

All of this private data is protected by cryptographic algorithms that are probably secure. Currently, cryptosystems that can be proven to be secure are far too unwieldy for practical use. So in lieu of a mathematical proof of security, cryptosystems that are practically secure are used. This means that it’s possible that shortcuts for defeating these ciphers exist, but no one’s been able to actualize them yet. Of course, there are also cryptosystems that aren’t secure at all. This could be due to the implementation, key size, or simply cryptanalytic weaknesses in the cipher itself. In 1997, under US law, the maximum allowable key size for encryption in exported software was 40 bits. This limit on key size makes the corresponding cipher insecure, as was shown by RSA Data Security and Ian Goldberg, a graduate student from the University of California, Berkeley. RSA posted a challenge to decipher a message encrypted with a 40-bit key, and three and a half hours later, Ian had done just that. This was strong evidence that 40-bit keys aren’t large enough for a secure cryptosystem.

**Information Theory**

Many of the concepts of cryptographic security stem from the mind of Claude Shannon. His ideas have influenced the field of cryptography greatly, especially the concepts of diffusion and confusion. Although the following concepts of unconditional security, one-time pads, quantum key distribution, and computational security weren’t actually conceived by Shannon, his ideas on perfect secrecy and information theory had great influence on the definitions of security.

**Unconditional Security**

A cryptographic system is considered to be unconditionally secure if it cannot be broken, even with infinite computational resources. This implies that cryptanalysis is impossible and that even if every possible key were tried in an exhaustive brute-force attack, it would be impossible to determine which key was the correct one.

**One-Time Pads**

One example of an unconditionally secure cryptosystem is the one-time pad. A one-time pad is a very simple cryptosystem that uses blocks of random data called pads. The pad must be at least as long as the plaintext message that is to be encoded, and the random data on the pad must be truly random, in the most literal sense of the word. Two identical pads are made: one for the recipient and one for the sender. To encode a message, the sender simply XORs each bit of the plaintext message with the corresponding bit of the pad. After the message is encoded, the pad is destroyed to ensure that it is only used once. Then the encrypted message can be sent to the recipient without fear of cryptanalysis, since the encrypted message cannot be broken without the pad. When the recipient receives the encrypted message, he also XORs each bit of the encrypted message with the corresponding bit of his pad to produce the original plaintext message.

While the one-time pad is theoretically impossible to break, in reality it’s not really all that practical to use. The security of the one-time pad hinges on the security of the pads. When the pads are distributed to the recipient and the sender, it is assumed that the pad transmission channel is secure. To be truly secure, this could involve a face-to-face meeting and exchange, but for convenience, the pad transmission may be facilitated via yet another cipher. The price of this convenience is that the entire system is now only as strong as the weakest link, which would be the cipher used to transmit the pads. Since the pad consists of random data of the same length as the plaintext message, and since the security of the whole system is only as good as the security of pad transmission, it usually makes more sense to just send the plaintext message encoded using the same cipher that would have been used to transmit the pad.

**Quantum Key Distribution**

The advent of quantum computation brings many interesting things to the field of cryptology. One of these is a practical implementation of the one time pad, made possible by quantum key distribution. The mystery of quantum entanglement can provide a reliable and secret method of sending a random string of bits that can be used as a key. This is done using non orthogonal quantum states in photons.

Without going into too much detail, the polarization of a photon is the oscillation direction of its electric field, which in this case can be along the horizontal, vertical, or one of the two diagonals. Nonorthogonal simply means the states are separated by an angle that isn’t 90 degrees. Curiously enough, it’s impossible to determine with certainty which of these four polarizations a single photon has. The rectilinear basis of the horizontal and vertical polarizations is incompatible with the diagonal basis of the two diagonal polarizations, so, due to the Heisenberg uncertainty principle, these two sets of polarizations cannot both be measured. Filters can be used to measure the polarizations— one for the rectilinear basis and one for the diagonal basis. When a photon passes through the correct filter, its polarization won’t change, but if it passes through the incorrect filter, its polarization will be randomly modified. This means that any eavesdropping attempt to measure the polarization of a photon has a good chance of scrambling the data, making it apparent that the channel isn’t secure.

These strange aspects of quantum mechanics were put to good use by Charles Bennett and Gilles Brassard in the first and probably best-known quantum key distribution scheme, called BB84. First, the sender and receiver agree on bit representation for the four polarizations, such that each basis has both 1 and 0. In this scheme, 1 could be represented by both vertical photon polarization and one of the diagonal polarizations (positive 45 degrees), while 0 could be represented by horizontal polarization and the other diagonal polarization (negative 45 degrees). This way, 1s and 0s can exist when the rectilinear polarization is measured and when the diagonal polarization is measured.

Then, the sender sends a stream of random photons, each coming from a randomly chosen basis (either rectilinear or diagonal), and these photons are recorded. When the receiver receives a photon, he also randomly chooses to measure it in either the rectilinear basis or the diagonal basis and records the result. Now, the two parties publicly compare which basis they used for each photon, and they keep only the data corresponding to the photons they both measured using the same basis. This doesn’t reveal the bit values of the photons, since there are both 1s and 0s in each basis. This makes up the key for the one-time pad.

Since an eavesdropper would ultimately end up changing the polarization of some of these photons and thus scramble the data, eavesdropping can be detected by computing the error rate of some random subset of the key. If there are too many errors, someone was probably eavesdropping, and the key should be thrown away. If not, the transmission of the key data was secure and private.

**Computational Security**

A cryptosystem is considered to be computationally secure if the best-known algorithm for breaking it requires an unreasonable amount of computational resources and time. This means that it is theoretically possible for an eavesdropper to break the encryption, but it is practically infeasible to actually do so, since the amount of time and resources necessary would far exceed the value of the encrypted information. Usually, the time needed to break a computationally secure cryptosystem is measured in tens of thousands of years, even with the assumption of a vast array of computational resources. Most modern cryptosystems fall into this category.

It’s important to note that the best-known algorithms for breaking cryptosystems are always evolving and being improved. Ideally, a cryptosystem would be defined as computationally secure if the best algorithm for breaking it requires an unreasonable amount of computational resources and time, but there is currently no way to prove that a given encryption-breaking algorithm is and always will be the best one. So, the current best-known algorithm is used instead to measure a cryptosystem’s security.

**Algorithmic Run Time**

Algorithmic run time is a bit different from the run time of a program. Since an algorithm is simply an idea, there’s no limit to the processing speed for evaluating the algorithm. This means that an expression of algorithmic run time in minutes or seconds is meaningless.

Without factors such as processor speed and architecture, the important unknown for an algorithm is input size. A sorting algorithm running on 1,000 elements will certainly take longer than the same sorting algorithm running on 10 elements. The input size is generally denoted by n, and each atomic step can be expressed as a number. The run time of a simple algorithm, such as the one that follows, can be expressed in terms of n.

This algorithm loops n times, each time doing two actions, and then does one last action, so the time complexity for this algorithm would be 2n + 1. A more complex algorithm with an additional nested loop tacked on, shown below, would have a time complexity of n2 + 2n + 1, since the new action is executed n2 times.

But this level of detail for time complexity is still too granular. For example, as n becomes larger, the relative difference between 2n + 5 and 2n + 365 becomes less and less. However, as n becomes larger, the relative difference between 2n2 + 5 and 2n + 5 becomes larger and larger. This type of generalized trending is what is most important to the run time of an algorithm.

Consider two algorithms, one with a time complexity of 2n + 365 and the other with 2n2 + 5. The 2n2 + 5 algorithm will outperform the 2n + 365 algorithm on small values for n. But for n = 30, both algorithms perform equally, and for all n greater than 30, the 2n + 365 algorithm will outperform the 2n2 + 5 algorithm. Since there are only 30 values for n in which the 2n2 + 5 algorithm performs better, but an infinite number of values for n in which the 2n + 365 algorithm performs better, the 2n + 365 algorithm is generally more efficient.

This means that, in general, the growth rate of the time complexity of an algorithm with respect to input size is more important than the time complexity for any fixed input. While this might not always hold true for specific real-world applications, this type of measurement of an algorithm’s efficiency tends to be true when averaged over all possible applications.

**Asymptotic Notation**

Asymptotic notation is a way to express an algorithm’s efficiency. It’s called asymptotic because it deals with the behavior of the algorithm as the input size approaches the asymptotic limit of infinity.

Returning to the examples of the 2n + 365 algorithm and the 2n2 + 5 algorithm, we determined that the 2n + 365 algorithm is generally more efficient because it follows the trend of n, while the 2n2 + 5 algorithm follows the general trend of n2 . This means that 2n + 365 is bounded above by a positive multiple of n for all sufficiently large n, and 2n2 + 5 is bounded above by a positive multiple of n2 for all sufficiently large n.

This sounds kind of confusing, but all it really means is that there exists a positive constant for the trend value and a lower bound on n, such that the trend value multiplied by the constant will always be greater than the time complexity for all n greater than the lower bound. In other words, 2n2 + 5 is in the order of n2 , and 2n + 365 is in the order of n. There’s a convenient mathematical notation for this, called big-oh notation, which looks like O(n2 ) to describe an algorithm that is in the order of n2 .

A simple way to convert an algorithm’s time complexity to big-oh notation is to simply look at the high-order terms, since these will be the terms that matter most as n becomes sufficiently large. So an algorithm with a time complexity of 3n4 + 43n3 + 763n + log n + 37 would be in the order of O(n4 ), and 54n7 + 23n4 + 4325 would be O(n7 ).

**Symmetric Encryption**

Symmetric ciphers are cryptosystems that use the same key to encrypt and decrypt messages. The encryption and decryption process is generally faster than with asymmetric encryption, but key distribution can be difficult. These ciphers are generally either block ciphers or stream ciphers. A block cipher operates on blocks of a fixed size, usually 64 or 128 bits. The same block of plaintext will always encrypt to the same ciphertext block, using the same key. DES, Blowfish, and AES (Rijndael) are all block ciphers. Stream ciphers generate a stream of pseudo-random bits, usually either one bit or byte at a time. This is called the keystream, and it is XORed with the plaintext. This is useful for encrypting continuous streams of data. RC4 and LSFR are examples of popular stream ciphers. RC4 will be discussed in depth in “Wireless 802.11b Encryption” on page 433.

DES and AES are both popular block ciphers. A lot of thought goes into the construction of block ciphers to make them resistant to known cryptanalytic attacks. Two concepts used repeatedly in block ciphers are confusion Cryptology 399 and diffusion. Confusion refers to methods used to hide relationships between the plaintext, the ciphertext, and the key. This means that the output bits must involve some complex transformation of the key and plaintext. Diffusion serves to spread the influence of the plaintext bits and the key bits over as much of the ciphertext as possible. Product ciphers combine both of these concepts by using various simple operations repeatedly. Both DES and AES are product ciphers.

DES and AES are both popular block ciphers. A lot of thought goes into the construction of block ciphers to make them resistant to known cryptanalytic attacks. Two concepts used repeatedly in block ciphers are confusion Cryptology 399 and diffusion. Confusion refers to methods used to hide relationships between the plaintext, the ciphertext, and the key. This means that the output bits must involve some complex transformation of the key and plaintext. Diffusion serves to spread the influence of the plaintext bits and the key bits over as much of the ciphertext as possible. Product ciphers combine both of these concepts by using various simple operations repeatedly. Both DES and AES are product ciphers.

The values for Li and Ri are as follows (the ⊕ symbol denotes the XOR operation):

_Li = Ri−1_

_Ri = Li−1 ⊕ f(Ri−1, Ki )_

DES uses 16 rounds of operation. This number was specifically chosen to defend against differential cryptanalysis. DES’s only real known weakness is its key size. Since the key is only 56 bits, the entire keyspace can be checked in an exhaustive brute-force attack in a few weeks on specialized hardware. Triple-DES fixes this problem by using two DES keys concatenated together for a total key size of 112 bits. Encryption is done by encrypting the plaintext block with the first key, then decrypting with the second key, and then encrypting again with the first key. Decryption is done analogously, but with the encryption and decryption operations switched. The added key size makes a brute-force effort exponentially more difficult. Most industry-standard block ciphers are resistant to all known forms of cryptanalysis, and the key sizes are usually too big to attempt an exhaustive brute-force attack. However, quantum computation provides some interesting possibilities, which are generally overhyped.

**Lov Grover’s Quantum Search Algorithm**

Quantum computation gives the promise of massive parallelism. A quantum computer can store many different states in a superposition (which can be thought of as an array) and perform calculations on all of them at once. This is ideal for brute forcing anything, including block ciphers. The superposition can be loaded up with every possible key, and then the encryption operation can be performed on all the keys at the same time. The tricky part is getting the right value out of the superposition. Quantum computers are weird in that when the superposition is looked at, the whole thing decoheres into a single state. Unfortunately, this decoherence is initially random, and the odds of decohering into each state in the superposition are equal.

Without some way to manipulate the odds of the superposition states, the same effect could be achieved by just guessing keys. Fortuitously, a man named Lov Grover came up with an algorithm that can manipulate the odds of the superposition states. This algorithm allows the odds of a certain desired state to increase while the others decrease. This process is repeated several times until the decohering of the superposition into the desired state is nearly guaranteed. This takes about steps.

Using some basic exponential math skills, you will notice that this just effectively halves the key size for an exhaustive brute-force attack. So, for the ultra paranoid, doubling the key size of a block cipher will make it resistant to even the theoretical possibilities of an exhaustive brute-force attack with a quantum computer.
