libvirt-vm
==========

Create a libvirt VM using virt-install.

Requirements
------------

Role assumes that the `virt-install` command is functional.  Typically this requires `libvirt`, `qemu-kvm`, and `virt-install` packages.  These also require hardware-assisted virtualization, as indicated by `vmx` or `smx` being present in the output of `lscpu`.

The controller host requires the `netaddr` python module to parse the IP address of the guest.


Role Variables
--------------

See `defaults/main.yml`

Dependencies
------------

None.

Example Playbook
----------------

    - name: install a VM on virthost
      hosts: virthost
      pre_tasks:
      - name: ensure virt packages are available on virthost
        package:
          name:
          - virt-install
          - libvirt
          - qemu-kvm
      roles:
         - role: libvirt-vm
           libvirt_vm_name: virtguest
           libvirt_vm_os_variant: rhel7.6

License
-------

Apache-2.0 or MIT or BSD-3-Clause

Author Information
------------------

[James Cassell](https://github.com/jamescassell)
