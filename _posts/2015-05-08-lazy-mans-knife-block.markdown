---
layout: post
title: Lazy Mans `knife-block`
---
# Lazy Mans `knife-block`
Manage multiple chef orgs/servers? Can't be bothered with the pain of installing
  a whole gem?  Want this all exposed by a shell variable for prompt hotness? In your `.chef/knife.rb`:

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


### Bonus tip
If you are a fish user add this somewhere to your `fish_prompt.fish`

```
  #CHEF
  set -g fish_color_chef blue
  if set -q CHEF_ENV
    printf '🍴 '
    set_color $fish_color_chef
    printf '%s ' $CHEF_ENV
    set_color normal
  end
```
I put it between the hostname and pwd.
Also if you are a fish user you can be super lazy and not even use caps in your
  enviroment variables; `set -x chefe orgname` works well. Don't forget the `-x` that's important
