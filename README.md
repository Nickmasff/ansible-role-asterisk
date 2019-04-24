# Ansible Role: Asterisk

[![Build Status](https://travis-ci.com/Nickmasff/ansible-role-asterisk.svg?branch=master)](https://travis-ci.com/Nickmasff/ansible-role-asterisk)

Installs and configures MySQL and Asterisk with ODBC realtime database driver.

Requirements
------------

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:


    - hosts: asterisk_machines
      roles:
        - role: nickmasff.asterisk
          become: yes

Install via ansible-galaxy
--------------------------

Use ansible galaxy to download this role with:

    ansible-galaxy install nickmasff.asterisk


## Dependencies

None.

## Example Playbook

    - hosts: asterisk_machines
      become: yes
      vars_files:
        - variables.yml
      roles:
        - { role: nickmasff.asterisk }
        

*Inside `variables.yml`*:
        
    mysql_user: user
    mysql_password: password
    mysql_database: asterisk
    mysql_priv: "asterisk.*:ALL"
    mysql_root_pass: password
    
    asterisk_username: asterisk
    asterisk_group: asterisk
    
    asterisk_config_path: ../../../files/asterisk/
    
    
    

## License

MIT / BSD

## Author Information

Nickmasff
nickmasff@yandex.ru

