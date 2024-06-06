### Pre-requisites Before Creating Infrastructure Setup in DigitalOcean
 
### **Create a Digital Ocean Token.**

1.  Login inside Digital ocean cloud
2.  In the left side, click on API 
3.  Click on Generate New token and save it somewhere for later use.

 Set this variables in terraform cloud at the Organization level

### **To create a reserved IP in DigitalOcean, follow these steps:**

1. Log In to DigitalOcean:

    - Go to the DigitalOcean website and log in to your account.

2. Navigate to Networking:

   - From the DigitalOcean dashboard, click on the "Networking" option in the left-hand menu.

3. Create a Reserved IP:

   - Under the "Networking" section, click on "Reserved IPs".

   - Click the "Create Reserved IP" button.

4. Assign the Reserved IP:

    - You will be prompted to choose the datacenter region where you want the reserved IP to be created.

    - Select the region where your droplets (virtual machines) are running or where you plan to create new ones.

    - Select the droplet you want to assign the reserved IP to, or choose to create a reserved IP without assigning it to a droplet initially.

4. Confirm and Create:

    - Click the "Reserve IP" button to create the reserved IP.

    - Once created, the reserved IP will appear in the list under the "Reserved IPs" section.


### Creating an SSH Key in DigitalOcean Cloud


1. Log In to DigitalOcean:

   - Go to the DigitalOcean website and log in to your account.

2. Navigate to Security:

   - From the DigitalOcean dashboard, click on the "Account" icon at the top right, then select "Security" from the dropdown menu.

3. Add an SSH Key:

   - Scroll down to the "SSH Keys" section.

   - Click on the "Add SSH Key" button.

   - Enter a name for your SSH key.

   - Copy the contents of your public SSH key (usually found in ~/.ssh/id_rsa.pub or created using ssh-keygen) and paste it into the provided field.

   - Click the "Add SSH Key" button to save it.

4. Get the SSH Key ID:

   - After adding the key, it will appear in the list of SSH keys.

   - The ID of the SSH key will be shown in the list alongside the key name.




We have already parameterized all the values. Any values that need to be passed externally should be set in the corresponding section within the env folder.



