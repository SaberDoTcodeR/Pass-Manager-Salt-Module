# Pass-Manager-Salt-Module
custom password manager saltstack module for huge networks to set passwords on a reguler algorithm

after adding this module to /srv/salt/_modules/ and putting your sha1 passphrase in pillar (simply by adding this to your /etc/pillar/top.sls

    base:

        '*':
  
            - data
    
and then adding this to /etc/pillar/data.sls

    pass: sha1 of your passphrase


and then use this command to sync your pillars 

    salt '*' saltutil.refresh_pillar
    
), then you can use this module to manage your passwords simply


password=first 15 chars of sha1(MinionIP+passphrase+nonce)

salt '*' pass_manager.getPassword "user" "passphrase"

salt '*' pass_manager.changePassword "user" "passphrase"

salt '*' pass_manager.getCurrentNonce "user" "passphrase"
