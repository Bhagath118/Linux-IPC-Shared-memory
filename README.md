# Linux-IPC-Shared-memory
Ex06-Linux IPC-Shared-memory

# AIM:
To Write a C program that illustrates two processes communicating using shared memory.

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - Shared Memory

### Step 3:

Execute the C Program for the desired output. 


# PROGRAM:
```
Developed By : A.BHAGATHKRISHNA
Reg no : 212223230029
```
## Write a C program that illustrates two processes communicating using shared memory.
```
#include <stdio.h>
#include <sys/ipc.h>
#include <sys/shm.h>

int main()
{
	// Generate a unique key using ftok
	key_t key = ftok("shmfile", 65);

	// Get an identifier for the shared memory segment using shmget
	int shmid = shmget(key, 1024, 0666 | IPC_CREAT);
      printf("Shared memory id = %d \n",shmid);
// Attach to the shared memory segment using shmat
	char* str = (char*)shmat(shmid, (void*)0, 0);
	
    printf("Write Data : ");
	fgets(str, 1024, stdin);

	printf("Data written in memory: %s\n", str);

	// Detach from the shared memory segment using shmdt
	shmdt(str);

	return 0;
}
```

## OUTPUT
![image](https://github.com/Bhagath118/Linux-IPC-Shared-memory/assets/147473779/76256943-fbd4-4ed2-8e81-d62caab77bb8)
![image](https://github.com/Bhagath118/Linux-IPC-Shared-memory/assets/147473779/665712d2-5f32-48fd-9d36-d2cbcbe85b62)
![image](https://github.com/Bhagath118/Linux-IPC-Shared-memory/assets/147473779/8ce760f5-b9d8-4f29-a342-896c6c5d1b87)



## RESULT:
The program is executed successfully.





