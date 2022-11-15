ansible_role_vsftpd
==============

This role perfoms the following actions on supported Operating Systems.

* Installs vsftpd.
* Configures vsftpd

Requirements
---------------

This role has been tested on the following Operating Systems.

* Red Hat 7
* Red Hat 8

Role variables
---------------

Variables used in the role:

    ansible_role_vsftpd_email_passwords  
    ansible_role_vsftpd_user_list  
    ansible_role_vsftpd_banned_emails  
    ansible_role_vsftpd_options  
    ansible_role_vsftpd_ftpusers  

`ansible_role_vsftpd_email_passwords` If `secure_email_list_enable` is set to YES in options this variable can provide a list of e-mail passwords for anonynmous logins, see http://vsftpd.beasts.org/vsftpd_conf.html for details.  
`ansible_role_vsftpd_user_list` if `user_list` is set to YES in options this variable holds a list of users which will be denied/accepted depending on the userlist_deny configuration option, see http://vsftpd.beasts.org/vsftpd_conf.html for details.  
`ansible_role_vsftpd_banned_emails` If `deny_email_enable` is set to YES in options this variable will hold a list of banned emails for anonymous logins, see http://vsftpd.beasts.org/vsftpd_conf.html for details.  
`ansible_role_vsftpd_options` User provided configurations that merges with Operating Systems defaults and vsftpd defaults, see http://vsftpd.beasts.org/vsftpd_conf.html for options. Make sure to quote any boolean value as in sample configuration.  
`ansible_role_vsftpd_ftpusers` 

Sample configuration
---------------

This section contains a sample configuration for this role.

```yaml

ansible_role_vsftpd_email_passwords:
  - secret_email_password1
  - secret_email_password1

ansible_role_vsftpd_user_list:
  - someuser1
  - someuser2
ansible_role_vsftpd_banned_emails:
  - banned1@email.localdomain
  - banned2@email.localdomain

ansible_role_vsftpd_ftpusers:
  - ftpuser1
  - ftpuser2

ansible_role_vsftpd_options:
  anon_umask: '63'
  anonymous_enable: 'YES'
  background: 'YES'
  banned_email_file: '/etc/vsftpd/banned_emails'
  chown_upload_mode: '384'
  chroot_local_user: 'YES'
  cmds_allowed: PWD,TYPE,PORT,STOR,PASV,LIST,CWD
  debug_ssl: 'False'
  deny_email_enable: 'YES'
  dirmessage_enable: 'NO'
  download_enable: 'NO'
  email_password_file: '/etc/vsftpd/email_passwords'
  file_open_mode: '438'
  hide_ids: 'NO'
  listen_ipv6: 'NO'
  listen: 'YES'
  local_root: '/home/$USER/ftp'
  local_umask: '63'
  pasv_max_port: 31000
  pasv_min_port: 30000
  secure_email_list_enable: 'YES'
  session_support: 'YES'
  user_sub_token: '$USER'
  userlist_deny: 'NO'
  userlist_enable: 'YES'
  userlist_file: '/etc/vsftpd.user_list'
  write_enable: 'YES'
  xferlog_std_format: 'NO'
  tcp_wrappers: 'NO'
```
