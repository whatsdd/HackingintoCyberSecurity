# Hacking

### **Hacking** <a href="#_61gtujtdzc0f" id="_61gtujtdzc0f"></a>

### Programming <a href="#_7vwzvdhotzp0" id="_7vwzvdhotzp0"></a>

While one group of hackers writes code and the other group exploits it, both use similar problem-solving techniques. Additionally, it suggests that having knowledge of both programming and exploitation can be beneficial for hackers as they complement each other. The passage also defines hacking as "the act of finding a clever and counterintuitive solution to a problem." This can be either in writing elegant and efficient code or finding vulnerabilities in existing programs and exploiting them.

It is also worth to mention that, this term is often associated with criminal activities and malicious use, but it's important to distinguish between hackers who use their knowledge to cause harm and "white-hat" hackers or security researchers who use their skills to find vulnerabilities in systems and help organizations fix them before any attackers can exploit them.

Programming hacks are creative solutions that use the rules of computer systems to improve efficiency or reduce code size, rather than to compromise security. These hacks often result in elegant, efficient and neat code. However, in the business world, the focus is often on producing functional code quickly, rather than on creating clever hacks or elegant solutions. This is because the power and memory of modern computers make small time and memory optimizations less significant in comparison to new features that can be marketed to increase revenue. As a result, spending time on clever hacks for optimization is not a priority.

Appreciation for the beauty and efficiency of programming is often limited to those who are passionate about the field, such as hobbyist computer users, exploit writers, and anyone who enjoys the challenge of finding the best possible solution. These individuals, known as hackers, are excited about programming and find joy in elegant code and clever hacks. They seek to get the most out of their systems and are not primarily driven by profit. As an understanding of programming is necessary to comprehend the ways in which programs can be exploited, it serves as a natural starting point for those interested in the field.

**What Is Programming?**

Programming is a simple and intuitive concept, in which a series of statements written in a specific language, called a program, are used to accomplish a task or set of tasks. Programs are prevalent in everyday life and are used by people of all technical abilities, from online driving directions and recipes, to football plays and even DNA sequences.

The ability to understand and follow a program is not limited to those with a technical background. Just like how someone who understands English can read and follow a set of driving directions written in English, even if they are not phrased eloquently, someone without technical knowledge can still understand and utilize a program, as long as its instructions are clear and easy to follow.

Computers do not understand human languages, they only understand machine language, which consists of raw bits and bytes. To command a computer to do something, the instructions must be written in machine language. However, machine language is complex, difficult to work with, and architecture specific, thus making it laborious and cumbersome to write programs in it. An assembler is a tool to bridge this gap and make it easier to write programs in machine language by translating assembly language, which uses names for instructions and variables rather than numbers, into machine-readable code. However, assembly language still requires a deep understanding of the low-level details of the specific architecture and is not easily portable across different architectures. Therefore, any program written in assembly language for one architecture would need to be rewritten to work on another architecture.

Another form of translator, known as a compiler, can help overcome these challenges. A compiler converts high-level languages into machine language, high-level languages are more intuitive than assembly language and can be converted into machine language for various types of processor architectures. This means that a program written in high-level language needs to be written only once, and it can then be compiled into machine language for various architectures. Examples of high-level languages include C, C++, and Fortran. Programs written in high-level languages are more readable and closer to English, however, they must follow a set of strict rules or the compiler will not be able to interpret it.

**Pseudo-code**

Pseudocode is another type of programming language used by programmers. It is a structured form of the English language, similar to a high-level language, that is not understood by compilers, assemblers, or computers. However, it is a helpful tool for arranging instructions. Pseudocode is not strictly defined and its structure may vary, it is not well-defined, as different programmers may write it differently. It serves as a bridge between English and high-level programming languages like C, and it can be useful for introducing fundamental programming concepts.

**Control Structures**

Control structures are fundamental building blocks in programming that allow for a deviation from the linear sequential execution of instructions in a program. They are necessary for most programs, which typically require more complexity beyond simple sequential instructions. Control structures, such as "continue on Main Street until you see a church on your right" or "if the street is blocked due to construction," change the flow of execution of the program to make it more adaptable and useful.

**If-Then-Else**

The "if-then-else" structure is one of the most commonly used control structures in programming. It allows for handling special cases, such as the Main Street being under construction in our driving directions example. The structure can be read as follows: "If a specific condition is met, execute a set of instructions (then); otherwise, execute a different set of instructions (else)". It is intuitive and allows for easy implementation of conditional statements in a program.

**While/Until Loops**

A while loop is another common control structure that allows for repeated execution of instructions. It is a type of loop, which is used to execute a set of instructions multiple times. A key aspect of loops is to have a stopping condition, otherwise, the loop will continue indefinitely. A while loop specifies that a set of instructions will be executed repeatedly as long as a specific condition is met. It allows the program to repeat a specific action until the condition is met or false.

**For Loops**

Another type of looping control structure is the "for loop". This structure is generally used when a programmer wants to execute a set of instructions for a specific number of iterations. The "for loop" allows you to define the number of iterations in advance. For example, the instruction "Drive straight down Destination Road for 5 miles" could be translated into a "for loop" which will execute a set of instruction five times, representing 5 miles.

### Exploitation <a href="#_gzp4iagl9z4i" id="_gzp4iagl9z4i"></a>

Program exploitation is a tactic commonly used by hackers to take advantage of weaknesses or vulnerabilities in a program. These vulnerabilities can be found in the design of the program or the environment it is operating in. The goal of exploitation is to manipulate the program to perform an action it was not intended to do, by taking advantage of these weaknesses. This can be done through finding and exploiting flaws or oversights in the program's design. The process of exploiting a program requires a deep understanding of how the program works, as well as a creative mind to find these vulnerabilities. Some vulnerabilities are caused by simple errors made by programmers, while others are more complex and require advanced techniques to exploit. In any case, program exploitation is a powerful tool that can be used to gain unauthorized access to sensitive information or perform other malicious actions.

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

Off-by-one errors, also known as fencepost errors, occur when a programmer miscalculates the number of items or spaces between items. This can result in the program processing too few or too many items. Improper Unicode expansion, on the other hand, happens when a program doesn't properly handle characters represented in Unicode, leading to unexpected behavior. These mistakes, although small, can have a significant impact on the security of a program as they can be exploited by malicious actors. The repetition of these types of mistakes across different code bases has led to the development of generalized exploit techniques that can be used to take advantage of them in a variety of situations.

Memory corruption exploits, such as buffer overflows and format string exploits, are common ways for attackers to take control of a program's execution flow by inserting malicious code into memory. This allows for arbitrary code execution, where the attacker can make the program perform any desired actions. These vulnerabilities occur when the program is not able to handle specific unexpected cases, which would usually cause the program to crash. However, by carefully manipulating the environment, attackers can prevent the crash and redirect the program's execution flow for their own gain.

**Buffer Overflows**

A buffer overflow occurs when more data is written to a memory location than it can hold, causing the excess data to overflow into adjacent memory locations. This can potentially cause the program to crash or even allow an attacker to execute malicious code. Buffer overflow vulnerabilities are particularly prevalent in C and C++ programs, as the language does not have built-in safety mechanisms to prevent this type of memory corruption. As a result, it is the responsibility of the programmer to ensure data integrity and properly check the size of buffers when handling input. This can make the resulting programs slower and more complex, but it is a necessary step to prevent these types of security vulnerabilities............................

A buffer overflow is a type of vulnerability in a computer program, where more data is sent to a buffer than it can hold. This can cause the program to crash or even execute malicious code, allowing an attacker to gain unauthorized access to the system. This is particularly prevalent in the C programming language, as it allows direct memory manipulation and does not have built-in safeguards to ensure that the contents of a variable fit into the allocated memory space. This can lead to memory overwriting and program crashes if not handled carefully by the programmer.

### Networking <a href="#_in8wisdkhmnl" id="_in8wisdkhmnl"></a>

Networking allows for communication and data transfer between computer systems, making it a crucial aspect for many applications such as email, web browsing, and instant messaging. However, it is important to note that networking protocols themselves can also have vulnerabilities. In this chapter, one will learn about using sockets to network applications and how to address common network security issues.

**OSI Model**

The OSI (Open Systems Interconnection) model is a framework used to understand and standardize how different communications protocols and technologies work together to enable network communication. It divides the process of transmitting data across a network into seven distinct layers, each with its own specific functions and responsibilities. The OSI model layers are:

**Physical Layer:**

This layer deals with the physical connection and transmission of data across the network. It includes the cables, switches, and other hardware used to transmit data.&#x20;

**Data Link Layer:**&#x20;

This layer establishes a link between devices on the same network and provides an error-free link for data to be transmitted across. It includes protocols such as Ethernet and ARP.&#x20;

**Network Layer:**&#x20;

This layer routes data packets between different networks. It includes protocols such as IP and ICMP.&#x20;

**Transport Layer:**&#x20;

This layer establishes a logical connection between different devices on the network and ensures the reliability of data transmission. It includes protocols such as TCP and UDP.&#x20;

**Session Layer:**&#x20;

This layer manages the sessions between different devices on the network. It includes the initiation, management, and termination of a connection between devices.&#x20;

**Presentation Layer:**&#x20;

This layer deals with the representation of data and how it is displayed to the user. It includes the translation and compression of data.&#x20;

**Application Layer:**&#x20;

This layer deals with the interactions between the applications running on different devices and the network. It includes the protocols that allow applications to access the network such as HTTP, FTP, and DNS. The OSI model provides a common framework that can be used to understand and troubleshoot network communication issues. It also helps in the development and standardization of network protocols as well as new technologies as it lays out how these technologies should interact with each other across the different layers of the model.

The physical layer of the internet protocol stack is responsible for the transmission of raw bits between devices. When browsing the web, the Ethernet cable and card make up this layer. The data link layer, which is also handled by Ethernet, allows for communication between devices on a LAN. However, it doesn't provide IP addresses yet. These addresses are assigned at the network layer, which is also responsible for moving data from one address to another. Together, these lower layers are able to send packets of data from one IP address to another. The transport layer, which for web traffic is TCP, ensures a seamless bidirectional connection. The term TCP/IP refers to the use of TCP on the transport layer and IP on the network layer. IPv4 is the most commonly used address scheme at this layer, in the form of XX.XX.XX.XX, while IPv6 also exist but have different addressing scheme.

The top layer of the OSI model, the application layer, uses HTTP (Hypertext Transfer Protocol) to facilitate communication when browsing the web. When a web browser on a network requests a webpage, it communicates with a web server located on a different network. In order for the data packets to reach their destination, they are encapsulated and passed down through the layers of the OSI model, starting at the application layer. The packets then pass through the router, which only needs to implement protocols up to the network layer, as it doesn't need to understand the contents of the packets. The router then sends the packets to the internet, where they reach the router of the destination network. This router encapsulates the packets with the necessary lower layer protocol headers, allowing the packets to reach their final destination.

![](<../.gitbook/assets/0 (3)>)

The process of packet encapsulation creates a complex language for devices on the internet and other networks to communicate with each other. This language is built into routers, firewalls, and operating systems, allowing them to understand and participate in the communication. Applications that rely on networking, such as web browsers and email clients, interface with the operating system to handle network communication. Since the operating system handles the technical details of packet encapsulation, it simplifies the task of creating network programs, which only need to interact with the OS's network interface.

**Sockets**

A socket is a standardized method of communicating through an operating system. It can be thought of as a connection endpoint, similar to a telephone jack on an operator's switchboard. Sockets serve as a high-level abstraction that shields programmers from the complexities of the OSI model. They allow for the sending and receiving of data over a network, with the transfer occurring at the session layer (layer 5) and the routing handled by the operating system at lower layers. There are various types of sockets, which define the structure of the transport layer (layer 4). The two most widely used are stream sockets and datagram sockets.

Stream sockets are a type of socket that provide reliable, two-way communication, similar to making a phone call. One side initiates a connection to the other and, once established, either side can communicate with the other. Stream sockets also confirm that the data has been received by its intended destination. They use Transmission Control Protocol (TCP), a standard communication protocol that operates at the transport layer (layer 4) of the OSI model. TCP ensures that data is transmitted in chunks called packets and that these packets arrive at the destination without errors and in the correct order, similar to words being spoken in the correct order during a phone conversation. Applications such as web servers, mail servers, and their respective client programs all use TCP and stream sockets for communication.

Another type of socket is a datagram socket, which is used for communication that is more like sending a letter than making a phone call. Communication using a datagram socket is one-way and unreliable. The order of the messages may not be maintained and it cannot be guaranteed that the messages will reach their destination. This is similar to mailing a letter - while the postal service is generally reliable, the internet is not. Datagram sockets use User Datagram Protocol (UDP) instead of TCP at the transport layer (layer 4). UDP is a very basic and lightweight protocol, which does not have built-in safeguards like TCP. It does not create a real connection but is just a simple method for sending data from one point to another. If a program needs to confirm that a packet has been received, it must be coded to send back an acknowledgement packet. This protocol have a lower overhead and are good for scenarios where packet loss is acceptable.

Datagram sockets and UDP are commonly used in networked games and streaming media because they allow developers to have more control over their communication needs without the added overhead of TCP. UDP is a connectionless protocol which means it does not establish a virtual circuit before sending data, this can result in lower latency and allows the developers to handle the reliability of the transmission on their own, which can be beneficial in real-time applications such as games and streaming media where the delay in transmission should be minimal.

**Socket Functions**

In C, Sockets are similar to files in that they both use file descriptors to identify themselves. In fact, sockets can be treated as files, allowing you to use the read() and write() functions to receive and send data using socket file descriptors. However, there are also functions that are specifically designed to work with sockets. These functions have their prototypes defined in the header file /usr/include/sys/sockets.h this header file contains the declarations for the functions, constants, and structures that are used for socket programming. Since sockets are handled differently than regular file I/O, these special functions are provided to handle the unique features and properties of sockets, such as creating, binding, and listening for incoming connections.

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

When a socket is created with the socket() function, it is necessary to specify the domain, type, and protocol of the socket. The domain, also known as the protocol family, refers to the set of protocols used by the socket for communication. Examples of protocol families include Internet Protocol (IP) which is used for communication on the Internet, and AX.25 which is used for amateur radio communication. These protocol families are defined in the header file bits/socket.h, which is automatically included when sys/socket.h is included in the program. It is important to note that the socket function only creates a socket and assign the properties specified on the function, but doesn't establish a connection, To establish a connection, typically you need to bind to a specific address and port and if it is a TCP socket, the listen to incoming connections and accept them.

### Shellcode <a href="#_k41aldojn210" id="_k41aldojn210"></a>

The shellcode utilized in our exploits has simply been a string of copied and pasted bytes. We have observed standard shell-spawning shellcode for local exploits and port-binding shellcode for remote ones. Shellcode is also sometimes referred to as an exploit payload, as it is a self-contained program that performs actions once a system has been compromised. It typically spawns a shell as a means of gaining control, but it can perform any function a program is capable of. However, for many hackers, understanding of shellcode only extends to copying and pasting bytes. This limits the potential of what can be achieved with shellcode. By creating custom shellcode, you have complete control over the exploited system. For example, you could add an admin account to /etc/passwd or automatically remove lines from log files. The possibilities are only limited by your imagination. Additionally, writing shellcode improves assembly language skills and employs a number of hacking techniques that are worth knowing.

**Assembly vs. C**

Shellcode is a set of machine-level instructions that is used to perform a specific task. These instructions are specific to a particular architecture and are typically written in assembly language. Although writing a program in assembly is different from writing it in C, many of the concepts are similar.

The operating system handles functions such as input and output, process management, file access, and network communication at the kernel level. Compiled C programs execute these tasks by making system calls to the kernel. The specific system calls available will vary depending on the operating system in use.

In C programming, standard libraries are often used to enhance convenience and portability. For example, a C program that uses the printf() function to output a string can be compiled on multiple systems without modification, as the library is responsible for knowing the appropriate system calls for various architectures. As a result, a C program compiled on an x86 processor will produce assembly language that is specific to that architecture.

On the other hand, assembly language is already specific to a particular processor architecture, thus portability is not possible. Instead of using standard libraries, direct kernel system calls must be made. To illustrate this point, we can compare a simple C program and its equivalent version written in x86 assembly.

When the compiled program is executed, the flow of execution goes through the standard I/O library, and finally, it makes a system call to display the string "Hello, world!" on the screen. The strace program can be used to trace a program's system calls. When applied to the compiled helloworld program, it shows all the system calls that the program makes.

The compiled program does more than just printing a string, the system calls at the start of the program set up the environment and memory for the program to run correctly. The important part is the write() system call, which actually outputs the string to the screen. The strace output also shows the arguments for the system call. The buf and count arguments are a pointer to the string and its length, respectively. The fd argument of 1 is a special standard file descriptor.

File descriptors are widely used in Unix systems for many purposes such as input, output, file access and network sockets. It is similar to a number given out at a coat check, where the first three file descriptor numbers (0, 1, and 2) are automatically used for standard input, output, and error. These values are standard and are defined in several locations, such as the /usr/include/unistd.h file.

**The Path to Shellcode**

Shellcode that is injected into a running program, where it takes over the program's execution, similar to how a virus infects a cell. Since shellcode is not an executable program, it does not have the benefit of having a defined layout of data in memory or being able to use other memory segments. The instructions in shellcode must be self-contained and be able to take over control of the processor regardless of its current state. This is commonly referred to as position-independent code.

In shellcode, the bytes for the string "Hello, world!" must be mixed together with the bytes for the assembly instructions, since there aren’t definable or predictable memory segments. To avoid EIP interpreting the string as instructions, the string is needs to be accessed through pointer. However, since the shellcode could be executed at any location in memory, the memory address of the string must be calculated relative to EIP. However, EIP cannot be accessed directly, so some sort of trick must be used to calculate the relative memory address.

**Assembly Instructions Using the Stack**

The stack is so integral to the x86 architecture that there are special instructions for its operations.

Stack-based exploits are made possible by the call and ret instructions, that are used by the CPU to manage function calls. When a function is called, the instruction pointer (EIP) is pushed to the stack, forming the stack frame, and the function is executed. After the function is finished, the ret instruction is used to pop the stored EIP from the stack, and the execution resumes at the instruction located at the popped address. By overwriting the return address stored on the stack before the ret instruction, it is possible to redirect the program's execution flow to a location specified by the attacker.

This technique can also be used to solve the problem of addressing inline string data. By placing the string directly after a call instruction, the address of the string will get pushed to the stack as the return address. Instead of calling a function, the attacker can jump past the string to a pop instruction that will take the address off the stack and into a register. This technique is demonstrated by the following assembly instructions.

The call instruction is used to jump the execution flow to a different location, which in this case, is located below the string. Additionally, it pushes the address of the instruction following the call instruction to the stack, which in this case, is the beginning of the string. Once the execution flow reaches the return instruction, the return address will be popped from the stack and placed in the appropriate register.

This technique of using the call and return instruction, along with utilizing the stack allows the attacker to execute position-independent code, meaning that it does not have a fixed location in memory. The raw instructions that are injected into an existing process are self-contained and can execute regardless of where the code is located in memory. As a result, these instructions cannot be linked into an executable and are not directly runnable as a standalone program.

The nasm assembler is a tool that converts assembly language into machine code, the instructions that can be executed by the CPU. On the other hand, ndisasm is a tool that converts machine code back into assembly language. These tools are useful for understanding the relationship between the machine code bytes and the assembly instructions. In the example provided, the disassembly instructions marked in bold are the bytes of the "Hello, world!" string interpreted as instructions.

The goal is to inject this shellcode into a running program, and redirect EIP (Instruction Pointer) to execute these instructions and the program will print out "Hello, world!" One example of a program that can be targeted for this exploit is the "notesearch" program.................................................

**Investigating with GDB**

**Since the notesearch program runs as root, we can’t debug it as a normal user. However, we also can’t just attach to a running copy of it, because it exits too quickly. Another way to debug programs is with core dumps. From a root prompt, the OS can be told to dump memory when the program crashes by using the command ulimit -c unlimited. This means that dumped core files are allowed to get as big as needed. Now, when the program crashes, the memory will be dumped to disk as a core file, which can be examined using GDB.**

**Once GDB is loaded, the disassembly style is switched to Intel. Since we are running GDB as root, the .gdbinit file won’t be used. The memory where the shellcode should be is examined. The instructions look incorrect, but it seems like the first incorrect call instruction is what caused the crash. At least, execution was redirected, but something went wrong with the shellcode bytes. Normally, strings are terminated by a null byte, but here, the shell was kind enough to remove these null bytes for us. This, however, totally destroys the meaning of the machine code. Often, shellcode will be injected into a process as a string, using functions like strcpy(). Such functions will simply terminate at the first null byte, producing incomplete and unusable shellcode in memory. In order for the shellcode to survive transit, it must be redesigned so it doesn’t contain any null bytes.**

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
