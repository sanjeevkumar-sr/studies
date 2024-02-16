this file containes yaml file for ansible automation 

    - name: Staging server Deployment
      hosts: testserver
      become: true
  # Install git 1.2
    
      tasks:
      
    - name: Install git 1.2
        package:
          name: git
          version: 1.2
          state: present
          
    - name: Clone a GitHub repository
        git:
          repo: <github url>
          dest: 
          clone: yes
          update: yes
          
     - name: Install httpd 2.4
        package:
          name: httpd
          version: 2.4
          state: present
  
    - name: Enable httpd service
        service:
          name: httpd
          state: started
          enabled: yes
  
      
    - name: Copy the index.html file to the httpd deployment path
        copy:
          src: /path/to/temp/directory/index.html
          dest: /var/www/html
  
    - name: Restart httpd
        service:
          name: httpd
          state: restarted
