
## Video 1

# Learning the command line

- Terminal helps us to interact with linux os
- echo command displays whatever given after it.
- Two types of users Normal user and super user(system admin)
- To become system admin/superuser/root, type in the command 'su'
- 'sudo' command followed by any command will be run by the superuser.

```
sudo cmd-name
```
- super-user mode can alter the linux os files .so use the commands carefully.
- 'ls' command displays all the files and directories in the specified path.
- Three compression utilities : gzip , zip , bzip2
- Create a folder using 'mkdir' command

```
mkdir san
```
- This creates a directory san in the given path.
- Get into a directory by using 'cd' command. ie. when you are in a directory containing the directory san, then use:

```
cd san
```

## Standard Output Redirection '>' 

- Redirects the output of a command to a new file, if the file is not present, then the file is created at that path.

```
echo hello > abc.txt
date > abc.txt
```
- This creates a file abc.txt and writes the output to the file.(overwites and not append)
- Standard Output Redirection using '>>' it does the same job as '>' the only difference is that instead of overwriting the file, it appends 
  the data to the file.

## Standard Input Redirection '<'  

- It takes the input from the file on right hand side and uses it on the command on left hand side.

```
./a.out < abc
```
- This means the compiled program takes the output from the file abc as the user input.

- Create a Single line file : shortcut method

```
echo content > filename
```
- In terminal, Ctrl + d is end of line ie. to end the terminal from reading data from user.
- 'cat' command with standard output redirection: It takes keyboard input and appends it to the file.

```
$ cat > filename
content
...
...
ctrl + d
```
- Removing a File using 'rm' command.

```
rm filename
```
### NOTE: 

- 'rm *' removes all files.
- 'rm -rf directory_name' removes all the files and subfolders under the directory name specified in the command recursively and forcefully.
- once removed, the files cannotbe retrieved when 'rm' command is used.
- Renaming a file using 'mv' command.

```
mv filename newfilename
```
- Create an empty file using 'touch' command.

```
touch filename
```
- Copy command 'cp' copies a file into a folder or a file to another file(need not exist- creates upon using the 'cp' command).

```
cp filename foldername
cp file1 file2
```
- 'pwd' to get the current directory.
- To go to root directory try ' cd .. ' until you reach root directory. or use 'cd /'


## Video 2

### Linking
  
  The standard library files are linked to the code we write by including headerfiles but this '.h' file does not contain 
  the codes for the standard library functions that we use in our code.This is a most common misconception, These '.h' files included 
  are just headers and they contain the details about the standard library files that needs to be linked inorder to run the program.
  in other words The '.h' files only contain the function declaration and not the function body. It is present only on standard c library 'libc'.
- Combining the machine code of the code we write with the machine code in standard libraries is called linking.
  there are 2 types 
  - <strong>Static linking</strong> 
   Static linking is the old method of linking used mainly in MDOS and other operating systems in that era.
   The libraries here are linked at the compile time.(in the disk)
   Every Executable code requires data from the standard libraries for execution, in static linking this is achieved by adding the required libraries
   with the code so that the final executable will have a size that is the sum of both the files (code + library files).
   Here one of the disadvantage is that the final code will use up more disk space.
   - <strong>Dynamic linking</strong>
   Dynamic linking is the method used in this era ie. in modern operating systems.Here the library files are not added to the code 
   we write physically but when the code we write 'a.c' is converted to machine code 'a.o', the library files required 
   are linked with the machine code to form 'a.out' which is dynamically linked. The machine code for all the libraries linked are 
   not physically present in the file a.out instead the details of the required libraries are stored as a note in the header of the file 'a.out'. 
   The header contains metadata(data about data). An example for metadata is an image file, the details of the image will be stored in the header.
   Now when executing the 'a.out' file, then the os sees the note on the header and it links the library files required in memory(RAM) at
   runtime.
   <strong>Disadvantages</strong>: When the code has to be run on other machines, the systems running this executable must have all the 
   libraries needed for its working, if not present, program will not work properly.
   Dynamic linking is becoming a problem when using cloud computing since the code has to be spread over many systems in the cloud. 
   <strong>NOTE</strong>: image, music and machine code files are non- ASCII ie they are not readable or printable.   
 
- Inside the root there are many folders:
- <strong>bin</strong> : It contains files having machine code for most of the commands used in the terminal.
  eg: ls,ln, which etc.
 - The details of the files in the bin folder can be known by using 'file' command.
 - ELF - Extended Linker Format which says that the files of this format contains machine code. 
 - 'ldd' command stands for 'linker dependency' it shows all the dynamically linked libraries of the file name given after ldd command.
   eg: 'ldd ln' shows all the dynamically linked libraries of the file 'ln'
 - Dynamically linked libraries have extension ' .so ' which stands for shared object. 
- <strong>boot</strong> : boot contains operating system kernel machine code.
  In linux the bootloader is 'grub' it loads up the kernel files required to run the system.
  If any of the files in boot are removed, next time you switch on the system, it wont boot up(nothing happens at the time 
  when we remove the files because all these files are already loaded on memory RAM)
  - Octal Dump 'od' command is used to read a file byte by byte, 16bit or 32 bit and write it as octal numbers.
  - 'objdump -D' pgm_name command performs disassembling ie converting machine code to assembly code.
  - 'man' command tells us about other commands and is present in 'usr/share/man'


## Video 3

- <strong>dev</strong>: All the files in dev are abstractions of peripheral devices. In linux or unix systems the peripheral devices 
  are connected and stored as files. these special files are stored in 'dev'.
  eg: keyboard, network card etc 
  - When we use 'ls -l' command, the files will be listed along with its user privilages ie the first 10 bit represents the type 
  of file, user privilages, group privilages and other's privilages. The first bit represents the type of file 
  d - directory
  '-' - file
  l - symbolic links
  c - character special : devices from which data is read as characters eg: keyboard are character special.
  b - block special: devices from which data is read as bytes, eg: network card are block special because data is read as block having size in bytes.

  - <strong>zero:</strong> It is a magical file that provides infinite stream of zeroes.(0000...). we cannot print the zeroes provided by this file on 
    the screen because the zeroes provided by this special file does not have an ASCII mapping inorder to see it printed on the screen, 
    it must be surrounded with quotes or must provide the ASCII value of zero that is '48'
  - <strong>null:</strong> it is also a magical file which discards unwanted output of our code, ie. when we write data to 'null' , 
    the data written vanishes.
- <strong>etc</strong>: The etc folder contains all the configuration files/data which are critical to working of the system.
  - hosts: The hosts file in etc contains the ip address and host name of the devices that can be reached using your system.
  - paswd: The paswd file contains all the accounts used in the system. In that list only root user has login privilage.
- <strong>home</strong>:It contains the details of users using the system.
- <strong>lib</strong>: It contains the files having '.so' extension ie the shared object which is the dynamically linked library files 
  and many other libraries. When we remove any files from this folder, then most of the commands and system functions will not work.
- <strong>lost+found</strong>: Used for troubleshooting purposes.
  The 'fsck' command is used to repair the file system if there is any problem.
  <strong>NOTE</strong>: The native linux file system is ext4
- <strong>proc</strong>: It refers to 'processes' ie. it has got files which has information about the processes running on the system.
  cpuinfo file in the proc folder shows the current cpu information.
  Some of the folders in proc folder are numbered folders. ie they are having a particular number and this number corresponds to the process id. 
  The numbered folder contains the details about the running proccess.
- <strong>sbin</strong>: Similar to 'bin' ie. it contains the machine code for commands that require admin/superuser privilage to run on the system
  example: partition, makefilesystem etc
- <strong>usr</strong>: The usr folder contains bin, lib, sbin which contains files which are not frequently used.
  It contains a folder called 'include' which contains all header files.
- <strong>var</strong>: The var folder contains log files, spool etc.
  log files store the diagonostic data written by a program occasionally while running.
  spool folder contains data in the form of a queue and sends it to the corresponding processes once the process is free.
  eg: printer spool : which stores the data to be printed as a queue in the spool and once the printer is free, it sends in the data to be printed.
  <strong>NOTE:</strong> The os kernel manages all of this with the help of drivers.
