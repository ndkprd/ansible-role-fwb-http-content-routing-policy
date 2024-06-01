Role Name
=========

Ansible role to manage Fortinet's FortiWeb HTTP Content Routing Policy.

Requirements
------------

- A FortiWeb admin account with ADOM write privilege.

Role Variables
--------------

The following variables are supported by this role:

| Variable | Type | Default Value | Description |
| --- | --- | --- | --- |
| fwb_http_content_routing_policies | dict | {} | HTTP Content Routing Policies. |
| fwb_http_content_routing_policies[x].name | str | "" | HTTP Content Routing Policy name. |
| fwb_http_content_routing_policies[x].server_pool | str | "" | HTTP Content Routing Policy server pool name. |
| fwb_http_content_routing_policies[x].http_content_routing_matchlist | array | [] | HTTP Content Routing Policy matchlist. |
| fwb_http_content_routing_policies[x].http_content_routing_matchlist[y].id | str | "" | HTTP Content Routing Policy matchlist id. |
| fwb_http_content_routing_policies[x].http_content_routing_matchlist[y].match_object | str | "http-host" | HTTP Content Routing Policy matchlist match object. |
| fwb_http_content_routing_policies[x].http_content_routing_matchlist[y].match_condition | str | "match-begin" | HTTP Content Routing Policy matchlist match condition. |
| fwb_http_content_routing_policies[x].http_content_routing_matchlist[y].match_expression | str | "" | HTTP Content Routing Policy matchlist match expression. |
| fwb_http_content_routing_policies[x].http_content_routing_matchlist[y].concatenate | str | "and" | HTTP Content Routing Policy matchlist concatenate. |

Dependencies
------------

This role only create the HTTP Content Routing Policy, which need Server Pool to be exist first. Luckily, FortiWeb already had modules for them, which you can check on their collection [repo](https://github.com/fortinet-ansible-dev/ansible-galaxy-fortiweb-collection).

Example Playbook
----------------

Check [tests folder](tests/).

Limitations
-----------

I don't find any way to get the value of HTTP Content Routing Policy matchlist, so the best I could do to implement somekind of idempotency is to compare the count of existing matchlist in the FortiWeb with the number of matchlist in the variable.

Also, since I couldn't check their value, I can't also find a good way to see if the value has changed or not, so for now the task result return will be always "ok" whether the value has changed or not.

License
-------

MIT License.

Author Information
------------------

[ndkprd.com](https://ndkprd.com)