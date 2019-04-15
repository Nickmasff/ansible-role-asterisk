# Ansible Role: Asterisk
=========

Installs and configures MySQL and Asterisk with ODBC realtime database driver.

Requirements
------------

No special requirements; note that this role requires root access, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:


    - hosts: asterisk_machine
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

    - hosts: asterisk_test_machines
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
    
    ari_user: ari_user
    ari_password: ari_password
      
    aors:
      name:
        contact: sip:test@mail.com@examle.com:5060
    
    endpoints:
      name:
        context: default
        disallow: all
        allow:
          - ulaw
          - alaw
        aors: name
        direct_media: "no"
    
    identifies:
      name:
        endpoint: name
        match: examle.com
    
    authorizations:
      name:
        auth_type: userpass
        password: password
        username: username
    
    registrations:
      name:
        outbound_auth: name
        server_uri: sip.test.com
        client_uri: sip:client@sip.test.com
        retry_interval: 60
        expiration: 120
        contact_user: name
    
    contexts:
      default:
        1:  200,1,Answer()
        2:  n,Playback(demo-congrats)
        3:  n,Hangup()
    
    
    

## License

MIT / BSD

## Author Information

Nickmasff
nickmasff@yandex.ru

