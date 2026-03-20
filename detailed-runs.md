# Details Runs of Each Playbook

## Openshift_scp Role

This role is entirely optional but is helpful for troubleshooting if network connectivity is lost from the node.  This will use a machineconfig to set the core user password.


~~~bash
$ ansible-playbook openshift_scp.yml 

PLAY [localhost] **************************************************************************************************************************************************************************************************

TASK [include_role : openshift_scp] *******************************************************************************************************************************************************************************
included: openshift_scp for bschmaus-thinkpadp1gen3.rmtusmn.csb

TASK [openshift_scp : Base64 Encode Password] *********************************************************************************************************************************************************************
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [openshift_scp : Deploy Core Password MachineConfig] *********************************************************************************************************************************************************
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : 30 second pause to let MCO start processing...] **********************************************************************************************************************************************
Pausing for 30 seconds
(ctrl+C then 'C' = continue early, ctrl+C then 'A' = abort)
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : Waiting Since 03:26:06 PM for the MachineConfig to Deploy] ***********************************************************************************************************************************
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:26:06 PM for the MachineConfig to Deploy (3000 retries left).
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

PLAY RECAP ********************************************************************************************************************************************************************************************************
bschmaus-thinkpadp1gen3.rmtusmn.csb : ok=5    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0  
~~~

## OpenShift_krn Role

This playbook configures hugepages, iommu and also blacklists kernel modules as a machineconfig.  This will cause the nodes to reboot and depending the number of nodes we might have to increase the wait delay.

~~~bash
$ ansible-playbook openshift_krn.yml 

PLAY [localhost] **************************************************************************************************************************************************************************************************

TASK [include_role : openshift_krn] *******************************************************************************************************************************************************************************
included: openshift_krn for bschmaus-thinkpadp1gen3.rmtusmn.csb

TASK [openshift_krn : Deploy Kernel Arguments MachineConfig] ******************************************************************************************************************************************************
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : 30 second pause to let MCO start processing...] **********************************************************************************************************************************************
Pausing for 30 seconds
(ctrl+C then 'C' = continue early, ctrl+C then 'A' = abort)
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : Waiting Since 03:30:58 PM for the MachineConfig to Deploy] ***********************************************************************************************************************************
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (3000 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2999 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2998 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2997 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2996 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2995 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2994 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2993 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2992 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2991 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2990 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2989 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2988 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2987 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2986 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2985 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2984 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2983 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2982 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2981 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2980 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2979 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2978 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2977 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:30:58 PM for the MachineConfig to Deploy (2976 retries left).
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

PLAY RECAP ********************************************************************************************************************************************************************************************************
bschmaus-thinkpadp1gen3.rmtusmn.csb : ok=4    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
~~~

## Openshift_rma Role

This playbook enable RDMA device namespace separation, which is essential for proper resource isolation in containerized environments.  This should not be used when using NVIDIA Network Operator in an rdmashared configuration.

~~~bash
$ ansible-playbook openshift_rma.yml 

PLAY [localhost] **************************************************************************************************************************************************************************************************

TASK [include_role : openshift_rma] *******************************************************************************************************************************************************************************
included: openshift_rma for bschmaus-thinkpadp1gen3.rmtusmn.csb

TASK [openshift_rma : IB Core RDMA Subsystem Namespace Contents] **************************************************************************************************************************************************
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [openshift_rma : Deploy RDMA Subsystem Namespace MachineConfig] **********************************************************************************************************************************************
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : 30 second pause to let MCO start processing...] **********************************************************************************************************************************************
Pausing for 30 seconds
(ctrl+C then 'C' = continue early, ctrl+C then 'A' = abort)
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : Waiting Since 03:43:52 PM for the MachineConfig to Deploy] ***********************************************************************************************************************************
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (3000 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2999 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2998 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2997 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2996 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2995 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2994 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2993 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2992 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2991 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2990 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2989 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2988 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2987 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2986 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2985 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2984 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2983 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2982 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2981 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2980 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2979 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2978 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2977 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2976 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2975 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2974 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2973 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2972 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2971 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:43:52 PM for the MachineConfig to Deploy (2970 retries left).
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

PLAY RECAP ********************************************************************************************************************************************************************************************************
bschmaus-thinkpadp1gen3.rmtusmn.csb : ok=5    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
~~~

## Openshift_udv Role

Not Started

## Openshift_nfd Role

This playbook will install Node Feature Discovery Operator 

~~~bash
$ ansible-playbook openshift_nfd.yml 

PLAY [localhost] **************************************************************************************************************************************************************************************************

TASK [include_role : openshift_nfd] *******************************************************************************************************************************************************************************
included: openshift_nfd for bschmaus-thinkpadp1gen3.rmtusmn.csb

TASK [openshift_nfd : Deploy NFD Operator] ************************************************************************************************************************************************************************
[WARNING]: Platform linux on host bschmaus-thinkpadp1gen3.rmtusmn.csb is using the discovered Python interpreter at /usr/bin/python3.13, but future installation of another Python interpreter could change the
meaning of that path. See https://docs.ansible.com/ansible-core/2.18/reference_appendices/interpreter_discovery.html for more information.
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : Waiting since 03:57:55 PM for CSV to appear] *************************************************************************************************************************************************
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting since 03:57:55 PM for CSV to appear (60 retries left).
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : Waiting since 03:58:17 PM for the operator to deploy] ****************************************************************************************************************************************
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [openshift_nfd : Deploy NFD Instance...] *********************************************************************************************************************************************************************
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : Waiting Since 03:58:18 PM for the Instance to Deploy] ****************************************************************************************************************************************
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

PLAY RECAP ********************************************************************************************************************************************************************************************************
bschmaus-thinkpadp1gen3.rmtusmn.csb : ok=6    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
~~~

## Openshift_sri Role

~~~bash
$ ansible-playbook openshift_sri.yml

PLAY [localhost] **************************************************************************************************************************************************************************************************

TASK [include_role : openshift_sri] *******************************************************************************************************************************************************************************
included: openshift_sri for bschmaus-thinkpadp1gen3.rmtusmn.csb

TASK [openshift_sri : Deploy SRIOV Operator] **********************************************************************************************************************************************************************
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : Waiting since 07:10:20 AM for CSV to appear] *************************************************************************************************************************************************
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : Waiting since 07:10:21 AM for the operator to deploy] ****************************************************************************************************************************************
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [openshift_sri : Deploy SRIOV Instance...] *******************************************************************************************************************************************************************
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

PLAY RECAP ********************************************************************************************************************************************************************************************************
bschmaus-thinkpadp1gen3.rmtusmn.csb : ok=5    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0  
~~~

## Openshift_nno Role

~~~bash
$ ansible-playbook openshift_nno.yml

PLAY [localhost] **************************************************************************************************************************************************************************************************

TASK [include_role : openshift_nno] *******************************************************************************************************************************************************************************
included: openshift_nno for bschmaus-thinkpadp1gen3.rmtusmn.csb

TASK [openshift_nno : Deploy NVIDIA Network Operator] *************************************************************************************************************************************************************
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : Waiting since 06:26:13 PM for CSV to appear] *************************************************************************************************************************************************
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting since 06:26:13 PM for CSV to appear (60 retries left).
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : Waiting since 06:26:35 PM for the operator to deploy] ****************************************************************************************************************************************
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [openshift_nno : Deploy NVIDIA Network Operator NicClusterPolicy...] *****************************************************************************************************************************************
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : Waiting Since 06:26:37 PM for the Instance to Deploy] ****************************************************************************************************************************************
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:26:37 PM for the Instance to Deploy (300 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:26:37 PM for the Instance to Deploy (299 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:26:37 PM for the Instance to Deploy (298 retries left).
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

PLAY RECAP ********************************************************************************************************************************************************************************************************
bschmaus-thinkpadp1gen3.rmtusmn.csb : ok=6    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0 
~~~

## Openshift_gpo Role

~~~bash
$ ansible-playbook openshift_gpo.yml 

PLAY [localhost] **************************************************************************************************************************************************************************************************

TASK [include_role : openshift_gpo] *******************************************************************************************************************************************************************************
included: openshift_gpo for bschmaus-thinkpadp1gen3.rmtusmn.csb

TASK [openshift_gpo : Deploy NVIDIA GPU Operator] *****************************************************************************************************************************************************************
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : Waiting since 06:42:27 PM for CSV to appear] *************************************************************************************************************************************************
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : Waiting since 06:42:28 PM for the operator to deploy] ****************************************************************************************************************************************
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [openshift_gpo : Deploy NVIDIA GPU Operator ClusterPolicy...] ************************************************************************************************************************************************
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : Waiting Since 06:42:30 PM for the Instance to Deploy] ****************************************************************************************************************************************
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:42:30 PM for the Instance to Deploy (300 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:42:30 PM for the Instance to Deploy (299 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:42:30 PM for the Instance to Deploy (298 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:42:30 PM for the Instance to Deploy (297 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:42:30 PM for the Instance to Deploy (296 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:42:30 PM for the Instance to Deploy (295 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:42:30 PM for the Instance to Deploy (294 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:42:30 PM for the Instance to Deploy (293 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:42:30 PM for the Instance to Deploy (292 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:42:30 PM for the Instance to Deploy (291 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:42:30 PM for the Instance to Deploy (290 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:42:30 PM for the Instance to Deploy (289 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:42:30 PM for the Instance to Deploy (288 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:42:30 PM for the Instance to Deploy (287 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:42:30 PM for the Instance to Deploy (286 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 06:42:30 PM for the Instance to Deploy (285 retries left).
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : Waiting Since 06:45:23 PM for the Instance to Deploy] ****************************************************************************************************************************************
skipping: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

PLAY RECAP ********************************************************************************************************************************************************************************************************
bschmaus-thinkpadp1gen3.rmtusmn.csb : ok=6    changed=1    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0 
~~~

## Openshift_ldp Role

~~~bash
$ ansible-playbook openshift_ldp.yml

PLAY [localhost] **************************************************************************************************************************************************************************************************

TASK [include_role : openshift_ldp] *******************************************************************************************************************************************************************************
[WARNING]: While constructing a mapping from /home/bschmaus/nvd-srv-26/ansible-spx/roles/openshift_ldp/defaults/main.yml, line 1, column 1, found a duplicate dict key (lldpd_image_name). Using last defined
value only.
included: openshift_ldp for bschmaus-thinkpadp1gen3.rmtusmn.csb

TASK [openshift_ldp : Create lldpd service account...] ************************************************************************************************************************************************************
[WARNING]: Platform linux on host bschmaus-thinkpadp1gen3.rmtusmn.csb is using the discovered Python interpreter at /usr/bin/python3.13, but future installation of another Python interpreter could change the
meaning of that path. See https://docs.ansible.com/ansible-core/2.18/reference_appendices/interpreter_discovery.html for more information.
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [openshift_ldp : Ensure lldpd service account exists...] *****************************************************************************************************************************************************
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [openshift_ldp : Create lldpd service account...] ************************************************************************************************************************************************************
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [openshift_ldp : Deploy Lldpd Daemonset...] ******************************************************************************************************************************************************************
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [openshift_ldp : Waiting Since 01:37:10 PM for the Daemonset to deploy...] ***********************************************************************************************************************************
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

PLAY RECAP ********************************************************************************************************************************************************************************************************
bschmaus-thinkpadp1gen3.rmtusmn.csb : ok=6    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
~~~

## Openshift_snp Role

~~~bash
$ ansible-playbook openshift_snp.yml 

PLAY [localhost] **************************************************************************************************************************************************************************************************

TASK [include_role : openshift_snp] *******************************************************************************************************************************************************************************
included: openshift_snp for bschmaus-thinkpadp1gen3.rmtusmn.csb

TASK [openshift_snp : Create Rail SNNP policies...] ***************************************************************************************************************************************************************
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb] => (item={'name': 'snnp-eth-rail0', 'mtu': 9216, 'pfname': 'eth_rail0', 'numvfs': 1, 'isrdma': True, 'linktype': 'eth', 'resourcename': 'eth_rail0'})
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb] => (item={'name': 'snnp-eth-rail1', 'mtu': 9216, 'pfname': 'eth_rail1', 'numvfs': 1, 'isrdma': True, 'linktype': 'eth', 'resourcename': 'eth_rail1'})
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb] => (item={'name': 'snnp-eth-rail2', 'mtu': 9216, 'pfname': 'eth_rail2', 'numvfs': 1, 'isrdma': True, 'linktype': 'eth', 'resourcename': 'eth_rail2'})
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb] => (item={'name': 'snnp-eth-rail3', 'mtu': 9216, 'pfname': 'eth_rail3', 'numvfs': 1, 'isrdma': True, 'linktype': 'eth', 'resourcename': 'eth_rail3'})
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb] => (item={'name': 'snnp-eth-rail4', 'mtu': 9216, 'pfname': 'eth_rail4', 'numvfs': 1, 'isrdma': True, 'linktype': 'eth', 'resourcename': 'eth_rail4'})
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb] => (item={'name': 'snnp-eth-rail5', 'mtu': 9216, 'pfname': 'eth_rail5', 'numvfs': 1, 'isrdma': True, 'linktype': 'eth', 'resourcename': 'eth_rail5'})
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb] => (item={'name': 'snnp-eth-rail6', 'mtu': 9216, 'pfname': 'eth_rail6', 'numvfs': 1, 'isrdma': True, 'linktype': 'eth', 'resourcename': 'eth_rail6'})
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb] => (item={'name': 'snnp-eth-rail7', 'mtu': 9216, 'pfname': 'eth_rail7', 'numvfs': 1, 'isrdma': True, 'linktype': 'eth', 'resourcename': 'eth_rail7'})

PLAY RECAP ********************************************************************************************************************************************************************************************************
bschmaus-thinkpadp1gen3.rmtusmn.csb : ok=2    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
~~~

## Openshift_off Role

~~~bash
$ ansible-playbook openshift_off.yml 

PLAY [localhost] **************************************************************************************************************************************************************************************************

TASK [include_role : openshift_off] *******************************************************************************************************************************************************************************
included: openshift_off for bschmaus-thinkpadp1gen3.rmtusmn.csb

TASK [openshift_off : Deploy OVS Offload...] **********************************************************************************************************************************************************************
[WARNING]: Platform linux on host bschmaus-thinkpadp1gen3.rmtusmn.csb is using the discovered Python interpreter at /usr/bin/python3.13, but future installation of another Python interpreter could change the
meaning of that path. See https://docs.ansible.com/ansible-core/2.18/reference_appendices/interpreter_discovery.html for more information.
changed: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : 30 second pause to let MCO start processing...] **********************************************************************************************************************************************
Pausing for 30 seconds
(ctrl+C then 'C' = continue early, ctrl+C then 'A' = abort)
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

TASK [common_tasks : Waiting Since 03:41:16 PM for the MachineConfig to Deploy] ***********************************************************************************************************************************
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (3000 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2999 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2998 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2997 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2996 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2995 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2994 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2993 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2992 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2991 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2990 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2989 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2988 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2987 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2986 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2985 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2984 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2983 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2982 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2981 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2980 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2979 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2978 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2977 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2976 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2975 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2974 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2973 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2972 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2971 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2970 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2969 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2968 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2967 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2966 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2965 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2964 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2963 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2962 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2961 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2960 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2959 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2958 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2957 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2956 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2955 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2954 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2953 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2952 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2951 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2950 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2949 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2948 retries left).
FAILED - RETRYING: [bschmaus-thinkpadp1gen3.rmtusmn.csb]: Waiting Since 03:41:16 PM for the MachineConfig to Deploy (2947 retries left).
ok: [bschmaus-thinkpadp1gen3.rmtusmn.csb]

PLAY RECAP ********************************************************************************************************************************************************************************************************
bschmaus-thinkpadp1gen3.rmtusmn.csb : ok=4    changed=1    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   
~~~
