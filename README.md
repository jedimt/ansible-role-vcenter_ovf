Ansible Role: Extract VCSA OVF
=========

Extracts the VCSA OVF file from the VCSA installer ISO for use in automated VCSA installs.

Requirements
------------

OVFTool 4.5+ must be installed on the target machine doing the extraction.

Role Variables
--------------

There are four variables included in the role:

    # Location of the vCenter ISO file
    vcenter_iso_folder: '/home/aaron/files/vmware'

    # Name of the ISO file
    vcenter_iso_file: 'VMware-VCSA-all-8.0.0-21216066.iso'

    # Filesystem mount point for the vCenter ISO image
    vcenter_tmp_mount_dir: '/tmp/iso'

    # OVFTool binary location
    ovftool_bin_path: '/home/aaron/files/vmware/ovftool/vmware-ovftool-lin/ovftool'

Dependencies
------------

None

Example Playbook
----------------

    # ===========================================================================
    # Create VCSA OVF file from vCenter ISO
    # ===========================================================================

    # Example invocation:
    # ansible-playbook -i inventory/linuxdev.yml playbooks/vcenter_ovf/create_vcsa_ovf.yml

    - name: Create VCSA OVF file
      hosts: all
      gather_facts: true
      tags: play_vcsa_ovf

      roles:
        - { role: ansible-role-vcenter-ovf, vcenter_iso_file: "VMware-VCSA-all-8.0.0-21216066.iso" }


License
-------

MIT

Author Information
------------------

Aaron Patten
aaronpatten@gmail.com
