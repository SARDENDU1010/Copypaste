#!/bin/bash


---
- name: Dummy Ansible Playbook
  hosts: all
  become: true

  vars:
    example_var: "Hello, Ansible"

  tasks:
    - name: Print a debug message
      debug:
        msg: "{{ example_var }}"

    - name: Ensure a dummy directory exists
      file:
        path: /tmp/dummy_directory
        state: directory
        mode: '0755'

    - name: Create a dummy file
      copy:
        content: "This is a dummy file created by Ansible.\n"
        dest: /tmp/dummy_directory/dummy.txt
        mode: '0644'
