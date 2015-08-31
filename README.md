# Ansible btsync

Install and manage a btsync server on Linux.

* download btsync
* install it on /usr/local
* create init service
* manage the config file with shared folders

# Role Variables

Also check the [btsync docs](http://sync-help.bittorrent.com/customer/portal/articles/1590260-preferences-explained).

**btsync_port**: Optional. Specify port to run on. Defaults to a random port at startup.

**btsync_upnp**: Optional. Whether or not to use uPNP. True by default

**btsync_user**: Required. The user who run the btsync daemon.

**btsync_download_limit**: Download limit, defaults to 0 (unlimted) in kB/s

**btsync_upload_limit**: Upload limit, defaults to 0 (unlimted) in kB/s

**btsync_check_for_updates**: "true" or "false", defaults to "false"

**disk_low_priority**: Set btsync to low disk priority, boolean, defaults to false

**lan_encrypt_data**: Encrypt data over lan, boolean, defaults to true

**rate_limit_local_peers**: Apply rate limit to local peers, boolean

**folder_rescan_interval**: Rescan every n seconds (defaults to 600)

**send_buf_size**: Decrease disk I/O by increasing memory usage, defaults to 10MB

**recv_buf_size**: Decrease disk I/O by increasing memory usage, defaults to 10MB

**sync_trash_ttl**: Optional, number of days before removed from trash (10 days default)

**external_port**: External port to use, defaults to 0 (dynamic)

**btsync_storage_path**: Default storage path, defaults to /var/lib/btsync/ (which is default on ubuntu)

**btsync_webui.address**: Optional. The ip to listen. Default 0.0.0.0.

**btsync_webui.port**: Optional. The port to listen. Default 8888

**btsync_webui.user**: Required. The username used to protect the webui

**btsync_webui.password**: Required. The password used to protect the webui

**btsync_webui.api_key**: Optional. The api key to use the btsync API (http://www.bittorrent.com/sync/developers/api)

**NOTE, when defining shared folders here, the webui will be disabled!**

**btsync_shared_folders**: Optional. An array of shared folders

**btsync_shared_folders.0.dir**: The path where the files will be synced

**btsync_shared_folders.0.secret**: The private key for the shared folder

For these options, look in the btsync docs:

**btsync_shared_folders.0.use_relay_server**: Optional
**btsync_shared_folders.0.use_tracker**: Optional
**btsync_shared_folders.0.use_dht**: Optional
**btsync_shared_folders.0.search_lan**: Optional
**btsync_shared_folders.0.known_hosts**: Optional. List of ipaddress:port of known hosts
**btsync_shared_folders.0.use_sync_trash**: Optional.

# Example

```yaml
  roles:
    - role: btsync
      btsync_user: thelocaluser
      btsync_webui:
        user: admin
        password: admin
        api_key: api_key
      btsync_shared_folders:
        - path: /path/to/shared/folder
          key: PRIVATEKEY
        - add more
```

# Dependencies

None

# License

(c) 2014 François de Metz

BSD
