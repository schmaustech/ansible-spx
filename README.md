# Ansible Playbooks for NVIDIA AI Deployment

**Goal**: The goal of this document is to build the common playbooks that are used when deploying the underlying infrastructure components for NVIDIA Network Operator and NVIDIA GPU Operator when used in a RDMA and/or Spectrum-X configuration. 

## Ansible Playbook Collections

Below is the list of Ansible playbooks in this repository and their function.  The grouping of playbooks can be run independently or as a whole.  Some of the playbooks can be used in other settings not just related to the general scope of this documents topic.

| **Playbook**    | **Description/Function**                                                                                                                             |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| openshift_nfd   | Installs the Node Feature Discovery Operator and configures an instance specific for NVIDIA network and GPU devices                                  |
| openshift_nms   | Installs the NMState Operator and configures the default nmstate instance                                                                            |
| openshift_nno   | Installs the NVIDIA Network Operator and configures either rdmashared, sriov or hostdevice depending on desired results                              |
| openshift_gpo   | Installs the NVIDIA GPU Operator and configures the GPU cluster policy for an RDMA setup                                                             |
| openshift_sriov | Installs                                                                                                                                             |
| openshift_blk   | Blacklists drivers that might interfere with NVIDIA Network Operator                                                                                 |

## Details
