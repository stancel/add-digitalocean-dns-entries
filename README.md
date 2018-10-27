add-digitalocean-dns-entries
=========

A role to add one or more DigitalOcean DNS entries to it so that is can be accessed at a given URL (`add_digitalocean_dns_entries_server_fqdn` variable) or list of given URL's (`add_digitalocean_dns_entries_sites_to_set_up` variable). 

Requirements
------------

You need the following items in order to use this role.
	
	* DigitalOcean account
	* API Key for your DO account stored in an environment variable called "DO_API_TOKEN"
	* The nameservers for the root domain that you are adding (server_fqdn) must be pointed to DigitalOcean's name servers


Role Variables
--------------

The Fully Qualified Domain Name to add to create an A record entry into the DigitalOcean DNS system. This role will also add an entry for this same FQDN, but that is pre-pended by a "www" subdomain.
```
	add_digitalocean_dns_entries_server_fqdn: "yourdomainhere.com"
```

An environment variable called DO_API_TOKEN that holds the value of your DigitalOcean API key.
```
	add_digitalocean_dns_entries_do_token: "{{ lookup('env', 'DO_API_TOKEN') }}"
```

Will you be passing a list of domains to add? The default is false.
```
	add_digitalocean_dns_entries_use_list_of_server_fqdn: false
```

List of Sites to setup DigitalOcean DNS Entries for. Not needed unless the "add_digitalocean_dns_entries_use_list_of_server_fqdn" variable is set to true. Default is false.
```
	add_digitalocean_dns_entries_sites_to_set_up:
	  - {
		  url: 'investmentappraiser.com',
		  need_to_register_dns: 'true',
		}
```

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:


	- hosts: localhost ansible_connection=local ansible_python_interpreter=python
	  vars_files:
	    - vars/main.yml
	  roles:
	    - { role: stancel.add_digitalocean_dns_entries }


or 


	- hosts: localhost ansible_connection=local ansible_python_interpreter=python 
	  vars:
		add_digitalocean_dns_entries_server_fqdn: "mydomain.com"
		add_digitalocean_dns_entries_do_token: "{{ lookup('env', 'DO_API_TOKEN') }}"
	  roles:
	    - { role: stancel.add_digitalocean_dns_entries }


License
-------

BSD

Author Information
------------------

[Brad Stancel](https://bradstancel.com)

