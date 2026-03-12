# Ansible Playbooks for NVIDIA AI Deployment

**Goal**: The goal of this document is to build the common playbooks that are used when deploying the underlying infrastructure components for NVIDIA Network Operator and NVIDIA GPU Operator when used in a RDMA and/or Spectrum-X configuration. 

## Ansible Playbook Collections

Below is the list of Ansible playbooks in this repository and their function.  The grouping of playbooks can be run independently or as a whole.  Some of the playbooks can be used in other settings not just related to the general scope of this documents topic.

| **Playbook**    | **Description/Function**                                                                                                       | **Status**          |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------|---------------------|
| openshift_nfd   | Installs the Node Feature Discovery Operator and configures an instance specific for NVIDIA network and GPU devices            |Complete             |
| openshift_nms   | Installs the NMState Operator and configures the default nmstate instance                                                      |Complete             |
| openshift_nno   | Installs the NVIDIA Network Operator and configures either rdmashared, sriov or hostdevice depending on desired results        |WIP                  |
| openshift_gpo   | Installs the NVIDIA GPU Operator and configures the GPU cluster policy for an RDMA setup                                       |WIP                  |
| openshift_sri   | Installs the SRIOV Operator and confgures initial components                                                                   |Not Started          |
| openshift_krn   | Configure kernel arguments and kernel module blacklist via machineconfig                                                       |Not Started          |
| openshift_scp   | This optional playbook will set core password via machineconfig                                                                |Complete             |
| openshift_rma   | Configure RDMA subsystem namespace awareness via machineconfig                                                                 |Not Started          |
| openshift_udv   | Configure UDEV rail rules machineconfig via machineconfig                                                                      |Not Started          |
| openshift_nmo   | Configure NVIDIA Maintenance Operator                                                                                          |Not Started          |

## Details
