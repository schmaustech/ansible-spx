# Ansible Playbooks for NVIDIA AI Deployment

**Goal**: The goal of this document is to build the common playbooks that are used when deploying the underlying infrastructure components for NVIDIA Network Operator and NVIDIA GPU Operator when used in a RDMA and/or Spectrum-X configuration. 

## Ansible Playbook Collections

Below is the list of Ansible playbooks in this repository and their function.  The grouping of playbooks can be run independently or as a whole.  Some of the playbooks can be used in other settings not just related to the general scope of this documents topic.

| **Playbook**    | **Description/Function**                                                                                                       | **Status**          |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------|---------------------|
| openshift_all   | Installs all the playbooks in the proper order for a full deployment of all components                                         |Not Started          |
| openshift_nfd   | Installs the Node Feature Discovery Operator and configures an instance specific for NVIDIA network and GPU devices            |Complete             |
| openshift_nms   | Installs the NMState Operator and configures the default nmstate instance                                                      |Complete             |
| openshift_nno   | Installs the NVIDIA Network Operator and configures either rdmashared, sriov or hostdevice depending on desired results        |WIP                  |
| openshift_gpo   | Installs the NVIDIA GPU Operator and configures the GPU cluster policy for an RDMA setup                                       |WIP                  |
| openshift_sri   | Installs the SRIOV Operator and confgures initial components                                                                   |WIP                  |
| openshift_krn   | Configure kernel arguments and kernel module blacklist via machineconfig                                                       |Complete             |
| openshift_scp   | This optional playbook will set core password via machineconfig                                                                |Complete             |
| openshift_rma   | Configure RDMA subsystem namespace awareness via machineconfig                                                                 |Complete             |
| openshift_udv   | Configure UDEV rail rules machineconfig via machineconfig                                                                      |Not Started          |
| openshift_nmo   | Configure NVIDIA Maintenance Operator                                                                                          |Not Started          |

## Details

## Openshift_scp Playbook Run

This playbook is entirely optional but is helpful for troubleshooting if network connectivity is lost from the node.  This will use a machineconfig to set the core user password.

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

## OpenShift_krn

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

## Openshift_rma

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

## Openshift_udv

Not Started

## OpenShift_nfd

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

## OpenShift_sri

~~~bash

~~~
