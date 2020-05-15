

# Free Range Routing (FRR) Collection
[![CI](https://zuul-ci.org/gated.svg)](https://dashboard.zuul.ansible.com/t/ansible/project/github.com/ansible-collections/frr.frr) <!--[![Codecov](https://img.shields.io/codecov/c/github/ansible-collections/vyos)](https://codecov.io/gh/ansible-collections/frr.frr)-->

The Ansible FRR collection includes a variety of Ansible content to help automate the management of FRR network appliances.

This collection has been tested against FRR 6.0.

### Supported connections
The FRR collection supports ``network_cli`` connections.

## Included content

Click the ``Content`` button to see the list of content included in this collection.

## Installing this collection

You can install the FRR collection with the Ansible Galaxy CLI:

    ansible-galaxy collection install frr.frr

You can also include it in a `requirements.yml` file and install it with `ansible-galaxy collection install -r requirements.yml`, using the format:

```yaml
---
collections:
  - name: frr.frr
```
## Using this collection

You can call modules by their Fully Qualified Collection Namespace (FQCN), such as `frr.frr.frr_bgp`.
The following example task replaces configuration changes in the existing configuration on a FRR network device, using the FQCN:

```yaml
---
  - name: configure global bgp as 64496
    frr.frr.frr_bgp:
      config:
        bgp_as: 64496
        router_id: 192.0.2.1
        log_neighbor_changes: True
        neighbors:
          - neighbor: 192.51.100.1
            remote_as: 64497
            timers:
              keepalive: 120
              holdtime: 360
          - neighbor: 198.51.100.2
            remote_as: 64498
        networks:
          - prefix: 192.0.2.0
            masklen: 24
            route_map: RMAP_1
          - prefix: 198.51.100.0
            masklen: 24
        address_family:
          - afi: ipv4
            safi: unicast
            redistribute:
              - protocol: ospf
                id: 223
                metric: 10
      operation: merge
```

Alternately, you can call modules by their short name if you list the `frr.frr` collection in the playbook's `collections`, as follows:

```yaml
---
- hosts: frr01
  gather_facts: false
  connection: network_cli

  collections:
    - frr.frr

  tasks:
    - name: Collect all facts from the device
      frr_facts:
        gather_subset: all
```


### See Also:

* [Ansible Using collections](https://docs.ansible.com/ansible/latest/user_guide/collections_using.html) for more details.

## Contributing to this collection

We welcome community contributions to this collection. If you find problems, please open an issue or create a PR against the [FRR collection repository](https://github.com/ansible-collections/frr.frr).

You can also join us on:

- Freenode IRC - ``#ansible-network`` Freenode channel
- Slack - https://ansiblenetwork.slack.com

See the [Ansible Community Guide](https://docs.ansible.com/ansible/latest/community/index.html) for details on contributing to Ansible.


## Changelogs
<!--Add a link to a changelog.md file or an external docsite to cover this information. -->

## Roadmap

<!-- Optional. Include the roadmap for this collection, and the proposed release/versioning strategy so users can anticipate the upgrade/update cycle. -->

## More information

- [Ansible network resources](https://docs.ansible.com/ansible/latest/network/getting_started/network_resources.html)
- [Ansible Collection overview](https://github.com/ansible-collections/overview)
- [Ansible User guide](https://docs.ansible.com/ansible/latest/user_guide/index.html)
- [Ansible Developer guide](https://docs.ansible.com/ansible/latest/dev_guide/index.html)
- [Ansible Community code of conduct](https://docs.ansible.com/ansible/latest/community/code_of_conduct.html)

## Licensing

GNU General Public License v3.0 or later.

See [LICENSE](https://www.gnu.org/licenses/gpl-3.0.txt) to see the full text.
