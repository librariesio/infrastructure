# Libraries.io Infrastructure

All the code and configuration for managing the servers that https://libraries.io runs on

## Setup

You'll need Ansible installed to run the playbooks, instructions here: http://docs.ansible.com/intro_installation.html

You will also need to have the GCP python dependencies for communicating with the API to load the inventories. To do this simply run `pipenv install` in the top level of the project. You will need to have Pipenv installed for this to work: https://pipenv.readthedocs.io/en/latest/

## Install required roles from Ansible Galaxy

    ansible-galaxy install -r ansible/requirements.yml

## Running playbooks

### main app

For deploying [Libraries.io](https://github.com/librariesio/libraries.io)

    ansible-playbook -i libraries_app.gcp.yml ansible/main-app.yml --vault-password-file ~/.vault_pass.txt

### cron machine

For running background jobs from [Libraries.io](https://github.com/librariesio/libraries.io)

    ansible-playbook -i libraries_cron.gcp.yml ansible/cron.yml --vault-password-file ~/.vault_pass.txt

### elasticsearch cluster

For the elasticsearch cluster for [Libraries.io](https://github.com/librariesio/libraries.io)

    ansible-playbook -i libraries_elasticsearch.gcp.yml ansible/elasticsearch.yml --vault-password-file ~/.vault_pass.txt

### memcached machines

For the memcached machines for [Libraries.io](https://github.com/librariesio/libraries.io)

    ansible-playbook -i libraries_memcached.gcp.yml ansible/memcached.yml --vault-password-file ~/.vault_pass.txt

### swift machine

For the swift parser server for [Libraries.io](https://github.com/librariesio/libraries.io)

    ansible-playbook ansible/swift.yml -i ansible/inventories/swift

### cocoapods machine

For the cocoapods server for [Libraries.io](https://github.com/librariesio/libraries.io)

    ansible-playbook ansible/cocoapods.yml -i ansible/inventories/cocoapods

### redis machine

For the redis server for [Libraries.io](https://github.com/librariesio/libraries.io)

    ansible-playbook -i libraries_redis.gcp.yml ansible/redis.yml --vault-password-file ~/.vault_pass.txt

### pip machine

For the pip server for [Libraries.io](https://github.com/librariesio/libraries.io)

    ansible-playbook ansible/pip.yml -i ansible/inventories/pip

### Note on Patches/Pull Requests

 * Fork the project.
 * Make your feature addition or bug fix.
 * Add tests for it. This is important so we don't break it in a future version unintentionally.
 * Send a pull request. Bonus points for topic branches.

### Code of Conduct

Please note that this project is released with a [Contributor Code of Conduct](CODE_OF_CONDUCT.md). By participating in this project you agree to abide by its terms.

## Copyright

Copyright (c) 2016 Andrew Nesbitt. See [LICENSE](https://github.com/librariesio/infrastructure/blob/master/LICENSE.txt) for details.
