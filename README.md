# **Ansible** 

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfrnoRa5cME0hZH6k1W1Ezg7KXVumofXZ8mR522mKkdUARglJ5fhNHmokHA4dbSEa2qwKFIH1NDQW_kmZNWDwRIupcQLpvzDLUJm3DoluV0O7s3HXP-LhevWCAKR5y1CqLJ54LOofJ-0PnYvu37bOP_YclT?key=moTFES1wrqeX_H27ZXliwQ)


## **What is Ansible?**

Ansible is a powerful automation tool designed for IT professionals, streamlining tasks like application deployment, server updates, cloud provisioning, and configuration management. Its agentless architecture simplifies deployment and eliminates additional security concerns. Ansible operates through simple, human-readable scripts, making version control easy and supporting the "infrastructure as code" movement, which treats IT maintenance like software development. While it excels in automation and DevOps, Ansible is also accessible to everyday users, allowing the configuration of multiple computers without requiring programming skills. Its straightforward instructions make it easy for both beginners and experts to use effectively.


## **How ansible work:-**

Ansible operates using a two-tier architecture consisting of a control node and managed nodes. The control node runs Ansible, while managed nodes are the devices being configured. Ansible connects to these nodes over a network and sends small programs called Ansible modules, which are executed via SSH. Once the tasks are completed, the modules are removed from the managed nodes. The primary requirement for this process is that the control node has login access to the managed nodes, typically achieved through SSH keys, though other authentication methods are also supported.


## **What Ansible does?**

Ansible simplifies system management through the use of Ansible modules, which model the desired state of a system. Each module specifies what should be true for a managed node. For example, if a systems administrator wants all workstations to have LibreOffice version X.Z installed, Ansible checks each node and updates any with an older version. This enables seamless overnight updates across an organization.

Using Ansible effectively means leveraging these modules to automate tasks across multiple computers. Users can explore existing modules for specific functions, and programmers have the option to create custom modules for specialized needs. If a custom module is widely useful, it can even be submitted to the Ansible project for others to use, enhancing the community's resources.


## **Ansible Playbook**

Ansible playbooks are configuration files written in YAML that outline the steps needed to achieve a desired state for managed nodes. They provide clear, human-readable instructions and are designed to be self-documenting. One of their key features is idempotence, meaning a playbook can be executed multiple times without causing adverse effects. If a playbook is run on a system that's already properly configured, the system remains unchanged, ensuring consistent and reliable management. This simplicity and reliability make playbooks an essential tool for automating IT tasks with Ansible.
## **Objective**

This playbook automates the process of:

- Extracting a ZIP file to a JAR file on the Ansible server.

-     Backing up the existing JAR file on the RHBK servers to /backup/\<timestamp>.

- Copying the new JAR file to the /opt/rhbk/providers directory on both RHBK servers.

- Running the kc.sh build script on the RHBK servers.

-  Restarting the RHBK servers.

## **I have a three server:-**

1. Ansible server

2. first-rhbk

3. second\_rhbk




**Ansible server**

```
sudo apt-add-repository ppa:ansible/ansible
```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdo-aUrrQiyelYSCZRTgenlsbgW_p9Oz-wxN5VL6AX3yIVy6FoWTiQYSkFIlxmJeA1V4tUmOqL0HbDk2rdsv1KH-VTvYLYBiiJ1jMR0t37YpGJWMEKcFgh_XAbIUngsh_OuY3-gBThu3JpmTC7AlKz49SdA?key=moTFES1wrqeX_H27ZXliwQ)

```
sudo apt update
```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdR37Tg4MRA1Xeom_QBtPu4fZdWh9Nkw_Rj97arFRyKsmd-9fSrZAsqi2XdA1tbXrsKqA3l0O_Gi2rMiK61XTsfh7f1LimgBz8Z9YQwfDo_EtyJeFLOtZZh77Vo-sJdZpIB_vw0UMh0SHcDRquczAiRbNIe?key=moTFES1wrqeX_H27ZXliwQ)

```
sudo apt install ansible
```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXf9tbK5Q_uhOzxjlWSpbZ7KKRpOsPbznGl9111D1BkqdK_jWVEEvFRN0WJufYMgpMGXivQKt0XIhKYptERjFKFxiWY0oSnDJ2na63vxIoV-WXg3kFfvI6FnnXzjrYFW_D_xCrDNWeXZb26ACqNp1_kpfD5i?key=moTFES1wrqeX_H27ZXliwQ)

```
ansible –version
```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfYJAHkXI4xRxytraSEocyFOGWEZ1IixJxLiA7VuV9GVVNcgtuD710lllLgIew-SM0iArSCi1t_eOcHXTyeprX-UkI1vkhyP2G2i_B-aKnMl1Vu0pOgRm8_bTVc3L-a-rmTUHhG9kEhSGQat4qMJax6v4z3?key=moTFES1wrqeX_H27ZXliwQ)

```
ssh-keygen
```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXcxCxo-P4PdCbVaUR83sepcnAKpkzdIAg6uNfw0_o53RCdMX-EhIRMoPeGmniyyyju-JQ5I2557pwFc2rcmrV8DtQ07LNApYywalZQC0it0gybHllMD71bX7sbEx-8ytVgBLC7FSFVhLkVihFjgpXUjLM-6?key=moTFES1wrqeX_H27ZXliwQ)

```
ssh-copy-id first-rhbk\@192.168.100.213
```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdsYCCcIaOVn4XoTcx-jBAzb7iKyBAUhcwI8FFmDSzWQi_0r_FvUeWSA245g30lgXpr2H1sE208QzxgqPbj6NTBwbfQ7ViCmJnw4MiJcBMl7XpwlGjafzRlIitv1vtktBwdPzyop1wTD8Lu6FJtaTm50x4o?key=moTFES1wrqeX_H27ZXliwQ)

```
ssh-copy-id second_rhbk@192.168.100.139
```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfY47xyp7SxJjakBJ4WYiCdPx1FwC35gd3UukkzcXoqY0CYPB-ldUhz-x3aMhtIZTpYBDA_VGnJFjj8hNuwIvf0i2g1aUtHm4MTCT7q9UrW1lcLtHnNlw4uj1MkniiU85hBRU4m0ou_kv_cUn5IrNn6iMHE?key=moTFES1wrqeX_H27ZXliwQ)

```
sudo apt install python3-pip
```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfBpbrNI6Lo976bFrzDLO3NJldgoC5Pqfgxm72QBm83Oc7a92BoRYIVzzIDoZQ2hkzK0oHOxMeQZy6qYq9e5eFARXDzlz2xbrNpOyEeV5vSepeaTTyl6Ibya--iPLMwXgJz4DsevljhctKSW9YxD-Emx5Fp?key=moTFES1wrqeX_H27ZXliwQ)

```
pip install --upgrade paramiko
```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeGAWV9s4yAZ_5_BfznSphlQbpcsaJU3xdG2JtNAVDTrSd642-iJJTUiDY6xH_2z1oryt0BM4OB1Q3mfd8yOaUjkt16pus3QUnao12NAGnz5Gh4uBIwHPQY9qYtIwwrWDM3o63F7y6p0sfctFehP9Wgzu07?key=moTFES1wrqeX_H27ZXliwQ)

```
pip install --upgrade cryptography
```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXc7PdIEtfDp2Gyi3WGs8AIhC3VEspho2duBFrt-1lacrF11Cok3Eh8kSUm9rFckz6ltlo-65U4XvHUeZL6hhm6Tx9hlq6sZeIwu57KkPXoN33eAvOtxy9N81DXCxRiuoQy-cW6Or4TX-JT0cdVwIYSIlBA?key=moTFES1wrqeX_H27ZXliwQ)

```
sudo visudo
```

Add configuration in the end

```
aman ALL=(ALL) NOPASSWD: ALL
```






```
sudo mkdir playbook
```

```
cd playbook
```

```
sudo mkdir -p Downloads/aman
```

```
sudo mkdir aman
```

Copy the zip file inside the folder aman

**Add configuration**

```
sudo vim /etc/ansible/hosts
```


```
 [webservers]

first-rhbk@192.168.100.213

 [webservers1]

second_rhbk@192.168.100.139
```



```
sudo vim main.yml
```

```
---

- name: Change the zip file & copy it

  hosts: localhost

  become: yes

  tasks:

    - name: Ensure Downloads directory exists

      file:

        path: /home/aman/Downloads

        state: directory

        mode: '0755'

    - name: Extract the zip file

      unarchive:

        src: /home/aman/Downloads/rhbk-24.0.3.zip

        dest: /home/aman/Downloads/aman/

        remote_src: yes

    - name: Change extracted files into a jar file

      command: jar cvf /home/aman/Downloads/aman/rhbk.jar -C /home/aman/Downloads/aman/rhbk-24.0.3 .

- name: Copy the jar file 

  hosts: all

  become: yes

  tasks:

- name: Manage JAR file on First server

  hosts: webservers

  become: yes

  tasks:

    - name: Check if the existing jar file exists on first server

      stat:

        path: /home/first-rhbk/Downloads/rhbk-24.0.3/providers/rhbk.jar

      register: rhbk\_file

    - name: Backup the existing jar file on first server

      copy:

        src: /home/first-rhbk/Downloads/rhbk-24.0.3/providers/rhbk.jar

        dest: "/home/first-rhbk/aman/backup/rhbk.jar.{{ ansible\_date\_time.iso8601 }}"

        remote\_src: yes

      when: rhbk\_file.stat.exists

    - name: Copy jar file from Ansible server to first server

      copy:

        src: /home/aman/Downloads/aman/rhbk.jar

        dest: /home/first-rhbk/Downloads/rhbk-24.0.3/providers/

    - name: Build file in first RHBK

      command: /home/first-rhbk/Downloads/rhbk-24.0.3/bin/kc.sh

    - name: Restart RHBK server

      command: systemctl restart nginx.service




- name: Second server

  hosts: webservers1

  become: yes

  tasks:

    - name: Check if the existing jar file exists on second server

      stat:

        path: /home/second\_rhbk/Downloads/rhbk-24.0.3/providers/rhbk.jar

      register: rhbk\_file

    - name: Backup the existing jar file on second server

      copy:

        src: /home/second\_rhbk/Downloads/rhbk-24.0.3/providers/rhbk.jar

        dest: "/home/second\_rhbk/aman/backup/rhbk.jar.{{ ansible\_date\_time.iso8601 }}"

        remote\_src: yes

      when: rhbk\_file.stat.exists

    - name: Copy jar file from Ansible server to second server

      copy:

        src: /home/aman/Downloads/aman/rhbk.jar

        dest: /home/second\_rhbk/Downloads/rhbk-24.0.3/providers/

    - name: Build file in second RHBK

      command: /home/second\_rhbk/Downloads/rhbk-24.0.3/bin/kc.sh

    - name: Restart rhbk server

      command: systemctl restart nginx.service







```


### **first-rhbk**

- Download rhbk-24.0.3.zip

  ```
  cd  Download
  ```

```
 unzip rhbk-24.0.3.zip
```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXe4naigAfTG0FJmbuQeDKkhBUuzi4BvyJM8c6qth-2C18GpZarPgK71hcnShismNy9Xk_XLjxPK59qgV6RoiSNMfLKxUr7Co45i-SMcf7epViAxbI1TC9wyvGiv13VMEiZTKxM2rG-wLNZiZiPcexW94_cU?key=moTFES1wrqeX_H27ZXliwQ)

```
sudo apt-cache search openjdk
```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeZTlseAZnMxqI7UXCEGaK-JPery6JofdiOHdhsgQrsLpZ_yRpJ-Jely-KDfy5mP5VcyG-i9lXpuI7zvWfxyOFt7KyDrRossMOrJKI-4pmSpEPwhLRrXxN-ZtTchQ0HT8V_IJgcVH3VwqGWu3hPnhYlY0pH?key=moTFES1wrqeX_H27ZXliwQ)

```
sudo apt install openjdk-17-jdk -y
```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXe8cY0Wv3Lqox0YcFrIxIA8Xn1aCSIleYaHqkVs9G_BUZjfKCkpevXRVIkXjNmLiEP4zQpJH8cnuVesOuMzZHlGFvsoTwAVFi9YWfGffsu2QE_vuIdeEfEI58cvn27UT54WjIstpeh_8lJLyP1frPHiK2AA?key=moTFES1wrqeX_H27ZXliwQ)

```
java -version
```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeUiqbdGdtYfwWsHNnO18qQ7rt-csmB9r12z-_vEA9drcfOqNOdnrXQ8DzDhGBUCvrdhatkZeJtG43uwcjzdDkp8KcBwsI-kUMkTDwItveKYAsflQ3Nvt7ubSx64HkCuKEO7IFdfHjx7EAAcZQwAU7-YniV?key=moTFES1wrqeX_H27ZXliwQ)


```
sudo apt install openssh-server
```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXef-mHWCFxK4JFi4-8a0B8Az7vkqGskVRJ9QLwDumUixF7SZJHUQMfd27qLlzrfxyHMrjg6LMYg_6r6NjpbTuRW6nk5jSMNSmEsuqnQKkHTif3Ht3Vt4Hb4x4nnGhZhEe1c-29p6V-9V73F8y-11YCvyNvy?key=moTFES1wrqeX_H27ZXliwQ)

```
sudo systemctl restart ssh

```
```
sudo systemctl status ssh 
```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXex0VtvGPgycDRwxovdBnAJQJ95C0pgiEzu3SGMsdKMZnsHsANXcei9fmQ6V0Zkku-HNv4NMlNi1L0cOG9aeIslIGEPewlcmWUAQc9mO2ptcTciR5Gghk5ZPFcwfLhKTmUPEcSYs_goDIumoOtUzZ3S3dKT?key=moTFES1wrqeX_H27ZXliwQ)

```
sudo mkdir -p aman/backup
```
```
sudo visudo

```


```
pushpender ALL=(ALL) NOPASSWD: ALL

```



### **second\_rhbk**

- Download rhbk-24.0.3.zip

```
 cd  Download

```

```
 unzip rhbk-24.0.3.zip

```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXe4naigAfTG0FJmbuQeDKkhBUuzi4BvyJM8c6qth-2C18GpZarPgK71hcnShismNy9Xk_XLjxPK59qgV6RoiSNMfLKxUr7Co45i-SMcf7epViAxbI1TC9wyvGiv13VMEiZTKxM2rG-wLNZiZiPcexW94_cU?key=moTFES1wrqeX_H27ZXliwQ)

```
sudo apt-cache search openjdk

```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeZTlseAZnMxqI7UXCEGaK-JPery6JofdiOHdhsgQrsLpZ_yRpJ-Jely-KDfy5mP5VcyG-i9lXpuI7zvWfxyOFt7KyDrRossMOrJKI-4pmSpEPwhLRrXxN-ZtTchQ0HT8V_IJgcVH3VwqGWu3hPnhYlY0pH?key=moTFES1wrqeX_H27ZXliwQ)


```
sudo apt install openjdk-17-jdk -y

```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXe8cY0Wv3Lqox0YcFrIxIA8Xn1aCSIleYaHqkVs9G_BUZjfKCkpevXRVIkXjNmLiEP4zQpJH8cnuVesOuMzZHlGFvsoTwAVFi9YWfGffsu2QE_vuIdeEfEI58cvn27UT54WjIstpeh_8lJLyP1frPHiK2AA?key=moTFES1wrqeX_H27ZXliwQ)

```
java -version

```
![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeUiqbdGdtYfwWsHNnO18qQ7rt-csmB9r12z-_vEA9drcfOqNOdnrXQ8DzDhGBUCvrdhatkZeJtG43uwcjzdDkp8KcBwsI-kUMkTDwItveKYAsflQ3Nvt7ubSx64HkCuKEO7IFdfHjx7EAAcZQwAU7-YniV?key=moTFES1wrqeX_H27ZXliwQ)



```
Sudo apt install openssh-server

```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXef-mHWCFxK4JFi4-8a0B8Az7vkqGskVRJ9QLwDumUixF7SZJHUQMfd27qLlzrfxyHMrjg6LMYg_6r6NjpbTuRW6nk5jSMNSmEsuqnQKkHTif3Ht3Vt4Hb4x4nnGhZhEe1c-29p6V-9V73F8y-11YCvyNvy?key=moTFES1wrqeX_H27ZXliwQ)

```
sudo systemctl restart ssh 

```
```
sudo systemctl status ssh 
```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXex0VtvGPgycDRwxovdBnAJQJ95C0pgiEzu3SGMsdKMZnsHsANXcei9fmQ6V0Zkku-HNv4NMlNi1L0cOG9aeIslIGEPewlcmWUAQc9mO2ptcTciR5Gghk5ZPFcwfLhKTmUPEcSYs_goDIumoOtUzZ3S3dKT?key=moTFES1wrqeX_H27ZXliwQ)

```
sudo mkdir -p aman/backup
```
```
sudo visudo

```
```
pushpender ALL=(ALL) NOPASSWD: ALL
```




## **Ansible Server**

```
cd playbook
```
```
ansible-playbook main.yml
```

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfZeYDNQGqWEyb52oFPb--t6CQ0XPOu_xHOO2iyE18h0zZnpdkTBWsihUTegoriSCC6zZJkFUGRmTQLvirZWLgWXlgoLXjs-D-GPZqPtB7Hhx8UqlJT7oRjxuTy1A90uOvul0A0cstTBSrsW4c1JMCRIyk?key=moTFES1wrqeX_H27ZXliwQ)

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfrJiH0XiC3GayU500Aa5O_zIgGqUDavUm9ix-82btNIeH85UybBqeZBO0MvuZxJYXN7omy0F8QRuQFbTais9SBjMCX3KstVcipM2QsEh6aI_D1d30WZv1RJ2Z9ioBclgu-8zMgeMLQmqSGCQYU_xE3fms?key=moTFES1wrqeX_H27ZXliwQ)




## **Conclusion**

This playbook simplifies the JAR deployment process for RHBK servers, ensuring that every step, from backup to deployment and restart, is automated and reliable. By using Ansible, you reduce the chances of manual errors and streamline the management of Keycloak deployments across multiple servers.
