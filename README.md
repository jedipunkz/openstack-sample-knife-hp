openstack-sample-knife-hp
=========================

OpenStack 書籍用 knife-hp 修正版

使用方法
----

    % sudo -i
    # wget https://github.com/jedipunkz/openstack-sample-knife-hp/raw/master/hp_server_create.rb
    # mv /var/lib/gems/1.9.1/gems/knife-hp-0.4.2/lib/chef/knife/hp_server_create.rb /var/lib/gems/1.9.1/gems/knife-hp-0.4.2/lib/chef/knife/hp_server_create.rb.org
    # cp hp_server_create.rb /var/lib/gems/1.9.1/gems/knife-hp-0.4.2/lib/chef/knife/hp_server_create.rb

前提条件
----

knife-hp 0.4.2 バージョンの場合の暫定対応である。
