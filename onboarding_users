#/bin/bash

# user file name declaration
file_name=name.csv
#group name declaration
group=developers
# setiing name of SSH directory for skel
SSH_SKEL=/etc/skel/.ssh
# public key file variable
AUTH=authorized_keys
# password 
PASSWORD=password

# check if group exists, create if not
if getent group $group > /dev/null;  then 
    echo "group already exist" 
else
    sudo groupadd $group
    echo "group succesfully created" 
fi

# add SSH folder to skel directory if not exist
if [[ -d "$SSH_SKEL" ]];  then
    echo "$SSH_SKELL already exists"
else   
    sudo mkdir -p $SSH_SKEL
    sudo bash -c "cat $AUTH >> $SSH_SKEL/auth_keys"
fi


#create user from filea
while IFS= read USERNAME; do 
    # check if username already exist
    if getent passwd $USERNAME > /dev/null; then 
        echo "User $USERNAME already exist" 
    else
        # creating user and adding to the group. -m create home directoty
        sudo useradd -m -g $group $USERNAME

        # creating password for the user. # double passord with \n becuase password is written twice. 
        echo "$USERNAME:$PASSWORD" | sudo chpasswd 

        # you can also set that the password has number of days to change the password
        # sudo passwd -n 5 $USERNAME

        # Set permissions for the .ssh directory and authorized_keys file
        sudo chmod 700 /home/$USERNAME/.ssh
        sudo chmod 644 /home/$USERNAME/.ssh/auth_keys

        echo "$USERNAME sucessfully created." 
    fi 
done < $file_name
exist 0
