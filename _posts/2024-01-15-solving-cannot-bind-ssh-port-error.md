# Solving the Cannot Bind SSH Port Error 

This can happen with SELinux systems like Rocky Linux. 

To fix:  
1- First, check if SELinux is running with "getenforce"
2- If it shows "enforcing", then do the following:
3- run `semanage port -a -t ssh_port_t -p tcp <new-port>` 
4- Verify the new port is added to existing allowed ports for ssh:
`semanage port -l | grep ssh `
5- You will see your new port in the output

Source(s): [The Geek Diary](https://www.thegeekdiary.com/error-bind-to-port-2222-on-0-0-0-0-failed-permission-denied-error-while-starting-sshd-service-on-centos-rhel/)
