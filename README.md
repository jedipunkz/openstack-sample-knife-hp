openstack-sample-knife-hp
=========================

OpenStack 書籍用 knife-hp 修正版

目的
----

opscode/knife-hp に下記の問題があったため修正した。

* サーバ作成時にネットワークが複数あるとネットワークの指定が出来ない

よって修正しこのレポジトリに収める。

パッチ
----

```diff
diff -u  ../knife-hp/lib/chef/knife/hp_server_create.rb hp_server_create.rb
--- ../knife-hp/lib/chef/knife/hp_server_create.rb  2014-10-18 19:01:33.000000000 +0900
+++ hp_server_create.rb 2014-10-19 19:44:13.000000000 +0900
@@ -185,7 +185,8 @@
           :image_id => locate_config_value(:image),
           :security_groups => config[:security_groups],
           :availability_zone => locate_config_value(:availability_zone),
-          :key_name => Chef::Config[:knife][:hp_ssh_key_id]
+          :key_name => Chef::Config[:knife][:hp_ssh_key_id],
+          :networks => locate_config_value(:networks)
         }
         unless locate_config_value(:networks).nil?
           server_def[:nics] = locate_config_value(:networks).map do |nic|
```

使用方法
----

    % sudo -i
    # wget https://github.com/jedipunkz/openstack-sample-knife-hp/raw/master/hp_server_create.rb
    # mv /var/lib/gems/1.9.1/gems/knife-hp-0.4.2/lib/chef/knife/hp_server_create.rb /var/lib/gems/1.9.1/gems/knife-hp-0.4.2/lib/chef/knife/hp_server_create.rb.org
    # cp hp_server_create.rb /var/lib/gems/1.9.1/gems/knife-hp-0.4.2/lib/chef/knife/hp_server_create.rb

前提条件
----

knife-hp 0.4.2 バージョンの場合の暫定対応である。
