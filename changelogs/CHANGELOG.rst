============================
Frr Collection Release Notes
============================

.. contents:: Topics


v1.0.3
======

Minor Changes
-------------

- Regenerated docs, add description to galaxy.yml and linked changelog to README (https://github.com/ansible-collections/frr.frr/pull/28)

v1.0.2
======

Release Summary
---------------

Rereleased 1.0.1 with updated changelog.

v1.0.1
======

Bugfixes
--------

- Makes sure that docstring and argspec are in sync and removes sanity ignores (https://github.com/ansible-collections/frr.frr/pull/23).
- Update docs after sanity fixes to modules.

v1.0.0
======

New Plugins
-----------

Cliconf
~~~~~~~

- frr - Use frr cliconf to run command on Free Range Routing platform

New Modules
-----------

- frr_bgp - Configure global BGP settings on Free Range Routing(FRR).
- frr_facts - Collect facts from remote devices running Free Range Routing (FRR).
