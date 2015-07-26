vagrant_up :
	vagrant up --no-provision

vagrant_provision :
	ln -s ../ ansible_gocd_server
	vagrant provision
	rm -f ansible_gocd_server

clean :
	vagrant destroy

test :	vagrant_up vagrant_provision

travis_ci:
	sudo apt-get install software-properties-common
	sudo apt-add-repository -y ppa:ansible/ansible
	sudo apt-get update
	sudo apt-get install -y ansible
	ln -s ../ ansible_gocd_server
	ansible-playbook -c local -e "hosts=127.0.0.1" test.yml
	rm -f ansible_gocd_server
