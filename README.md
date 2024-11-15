
# Linux-File-IO-Systems-locking
Ex07-Linux File-IO Systems-locking
# AIM:
To Write a C program that illustrates files copying and locking

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux IO Systems locking

### Step 3:

Execute the C Program for the desired output. 

# PROGRAM:

## 1.To Write a C program that illustrates files copying 
```
#include <unistd.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <stdlib.h>
int main()
{
char block[1024];
int in, out;
int nread;
in = open("filecopy.c", O_RDONLY);
out = open("file.out", O_WRONLY|O_CREAT, S_IRUSR|S_IWUSR);
while((nread = read(in,block,sizeof(block))) > 0)
write(out,block,nread);
exit(0);}
```






## 2.To Write a C program that illustrates files locking
```

#include <fcntl.h>
#include <stdio.h>
#include <string.h>
#include <unistd.h>
#include <sys/file.h>
int main (int argc, char* argv[])
{ char* file = argv[1];
 int fd;
 struct flock lock;
 printf ("opening %s\n", file);
 /* Open a file descriptor to the file. */
 fd = open (file, O_WRONLY);
// acquire shared lock
if (flock(fd, LOCK_SH) == -1) {
    printf("error");
}else
{printf("Acquiring shared lock using flock");
}
getchar();
// non-atomically upgrade to exclusive lock
// do it in non-blocking mode, i.e. fail if can't upgrade immediately
if (flock(fd, LOCK_EX | LOCK_NB) == -1) {
    printf("error");
}else
{printf("Acquiring exclusive lock using flock");}
getchar();
// release lock
// lock is also released automatically when close() is called or process exits
if (flock(fd, LOCK_UN) == -1) {
    printf("error");
}else{
printf("unlocking");
}
getchar();
close (fd);
return 0;
}


```



## OUTPUT

## 1.Output of C program that illustrates files copying:

![WhatsApp Image 2024-10-26 at 16 03 17_bf3427e3](https://github.com/user-attachments/assets/fee1860a-4225-4bed-a486-7262d33f127f)
![WhatsApp Image 2024-10-26 at 16 03 27_0ca94de6](https://github.com/user-attachments/assets/7f08a891-c50d-4355-8831-4d7170d1bdf9)

## 2.To Write a C program that illustrates files locking:

![WhatsApp Image 2024-10-26 at 16 16 23_4d967f59](https://github.com/user-attachments/assets/88e3fced-66e6-4439-9056-8ef53c0aab25)
![WhatsApp Image 2024-10-26 at 16 16 59_6c54f6a2](https://github.com/user-attachments/assets/d9507101-e2c0-4875-9c27-f42dee644c74)


# RESULT:
The programs are executed successfully.
