# 🤩How to Remove Fedora Cleanly from Dual Boot System

## 💻 Run cmd as admin:

### Step 1️⃣:

```
         bcdedit /enum firmware
```

### Step 2️⃣:
Select EFI firmware identifier e.g. {abcdxxxx}

### Step 3️⃣:
Delete the entry from store:

```
         bcdedit /delete {abcdxxxx}
```

### Step 4️⃣: Remove the Linux partition from disk management

### Step 5️⃣ (Optional):
Delete files for the EFI partition of the deleted entry:

🟢5-1:
```
         diskpart
```
🟢5-2:  
```       
         list disk
```
🟢5-3:  
```      
         select disk [1]
```
Replace [1] with the correct number from "list disk"

🟢5-4:  
```
         list vol
```         
🟢5-5: 
 ```  
         select Volume [0]
```
Replace [0] with number for the volume that is 100 MB (System Partition)

🟢5-6: 
```   
         assign letter z
```         
z can be any letter 

🟢5-7: 

Exit diskpart

🟢5-8:

 Go to z
```
         z:
```
🟢5-9: 
```
         dir
```         
🟢5-10: 

Go to EFI directory
```
         cd EFI
```
🟢5-11: 

Find the directory for the deleted Linux distro (e.g. Ubuntu)

🟢5-12: 

Remove the directory:
```
         rmdir /s Ubuntu
```        
(Replace Ubuntu with actual distro name)
