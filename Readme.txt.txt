Configure Ansible Host in Azure Devops  ----  https://www.youtube.com/watch?v=yRPEJDcTxuk

1] Download and install ansible and git in Ansible base machine

wget https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm -- download package 

sudo yum update -y -- to update the machine with apps

sudo yum install ansible git  -- install ansible and git

ansible --version, git -- version   --- check and confirm if ansible and got is installed


2] Download and install Azure VSTS agent on base machine

-- go to Azure devops->Agent Pools->Default and select Linux
-- copy the link and paste it base machine with command:
	wget link  --> enter
-- extract and install agent by command:
	tar zxvf (unzip) vsts-agent
-- install agent dependencies:
	sudo ./installdependencies.sh
-- configure the agent and enter the required details
	./config.sh
-- give project URL
-- give Personal Access Token (go to azure devops-> user setting-> Personal Access Token-> generate new token-> give full access)
-- run the agent to make it online by command: ./run.sh


3] Make SSH connection with ssh keygen

-- Add private IPs of ansible nodes by command: sudo vi /etc/ansible/hosts
-- generate ssh keygen by command: ssh-keygen
-- copy key gen id to nodes by command: ssh-copy-id privateIPofnode
-- run command to check ssh connection: ssh privateIPofnode and ansible -m ping all (if all nodes responds as 'pong' connection is successfull)