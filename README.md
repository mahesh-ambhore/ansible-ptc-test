Before executing this playbook. We need to prepare the Docker container. To prepare docker container execute below steps.

1)Clone the git repo using git clone https://github.com/mahesh-ambhore/ansible-ptc-test.git
2)Go to "ansible-ptc-test" directory .
3)Execute docker build --tag="ubuntu-ssh:1.0" . command to create docker image from docker file.
4)execute docker run -it --name myubuntussh ubuntu-ssh:1.0 /bin/bash command to create docker container from the currently created image.
5)create docker user using and add to the sudo group
  “adduser docker”.
  “usermod -aG sudo docker”.
6)edit Port from 22 to 2222 from "/etc/ssh/ssh_config" and restart ssh service using sudo service ssh restart command
7)open new terminal window.
8)execute “docker container inspect myubuntussh” to get the conatainer info and get “IPAddress” from command output.
9)execute “ ssh-copy-id docker@ IPAddress ” to communicate docker container using ssh.
10)Execute playbook using below command .
    Go to playbook folder using cd playbook and execute below command.
    ansible-playbook -i hosts playbook.yml
11) open /etc/hosts and below entry in hosts file.
      <container ip address> example.com
       <container ip address> test.com
         
 12) Open the browser and check url "example.com" and "test.com"
