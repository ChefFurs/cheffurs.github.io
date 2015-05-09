---
layout: post
title: Lazy Mans `knife-block`
---
# Lazy Mans `knife-block`
Manage multiple chef orgs/servers? Can't be bothered with the pain of installing
  a whole gem?  Add this to your knife.rb:

```
organization = ENV['CHEF_ENV'] || "a-sane-default"
case organization
  when "foo"
    validation_key  "#{config_dir}/foo-validator"
    client_key      "#{config_dir}/bob-foo.pem"
    chef_server_url "https://api.opscode.com/organizations/foo"
  when "bar"
    validation_key  "#{config_dir}/bar-validator"
    client_key      "#{config_dir}/bob-bar.pem"
    chef_server_url "https://api.myorg.net/organizations/bar"
  when "a-sane-default"
    validation_key  "#{config_dir}/default-validator"
    client_key      "#{config_dir}/bob-default.pem"
    chef_server_url "https://api.otherorg.net/organizations/bar"
```
etc, etc
