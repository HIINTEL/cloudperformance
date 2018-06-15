# cloud performance

add cloud performances


# use ec2_... cloud cache variables if single
``` bash
ansible -i ../../ec2.py  -m debug -a "var=hostvars[inventory_hostname]" vpnas.cloud.zingbox.com
```

# find undefined
``` bash
cat zc-nonenv.yml

---
- hosts: all
  gather_facts: no
  tasks:
    - include_vars:
        file: "~/aws.yml"

    - name: login to zc_env undefined 
      shell: |
        echo "{{ ec2_tag_zc_env }}"
      environment:
        AWS_ACCESS_KEY_ID: "{{ AWS_ACCESS_KEY_ID }}"
        AWS_SECRET_ACCESS_KEY: "{{ AWS_SECRET_ACCESS_KEY }}"
        AWS_DEFAULT_REGION: "{{ reg }}"
      when: ec2_tag_zc_env is not defined

```
