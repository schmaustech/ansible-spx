# Ansible Playbooks for NVIDIA AI Deployment

**Goal**: The goal of this document is to build the common playbooks that are used when deploying the underlying infrastructure components for NVIDIA Network Operator and NVIDIA GPU Operator when used in a RDMA and/or Spectrum-X configuration. 

## Ansible Playbook Collections

Below is the list of Ansible playbooks in this repository and their function.

| **Playbook**    | **Description/Function**                                                                                                       | **Status**          |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------|---------------------|
| openshift_all   | Installs all the playbooks in the proper order for a full deployment of all components                                         |Not Started          |
| openshift_scp   | This optional playbook will set core password via machineconfig                                                                |Complete             |
| openshift_krn   | Configure kernel arguments and kernel module blacklist via machineconfig                                                       |Complete             |
| openshift_rma   | Configure RDMA subsystem namespace awareness via machineconfig                                                                 |Complete             |
| openshift_udv   | Configure UDEV rail rules machineconfig via machineconfig                                                                      |Not Started          |
| openshift_nfd   | Installs the Node Feature Discovery Operator and configures an instance specific for NVIDIA network and GPU devices            |Complete             |
| openshift_nms   | Installs the NMState Operator and configures the default nmstate instance                                                      |Complete             |
| openshift_sri   | Installs the SRIOV Operator and confgures initial components                                                                   |Complete             |
| openshift_nno   | Installs the NVIDIA Network Operator and configures either rdmashared, sriov or hostdevice depending on desired results        |Complete             |
| openshift_gpo   | Installs the NVIDIA GPU Operator and configures the GPU cluster policy for an RDMA setup                                       |Complete             |
| openshift_nmo   | Configure NVIDIA Maintenance Operator                                                                                          |Not Started          |
| openshift_off   | Configure OVS offload                                                                                                          |Complete             |
| openshift_ldp   | Configure the lldpd daemonset which is required for Spectrum-X topology validation                                             |Complete             |
| openshift_ngx   | Configure Nginx for network card firmware serving                                                                              |Not Started          |
| openshift_cnv   | Installs the OpenShift Virtualization Operator and configures initial setup (not required for Spectrum-X)                      |WIP                  |
| openshift_snp   | Creates the rail SriovNetworkNodePolicies                                                                                      |Complete             |


## Playbook Details 

Each playbook is broken down into a role that can independently be run and in some cases be used for other deployments beside Spectrum-X.  Each role has the following structure in the repository:

* defaults/main.yml: This is where default variables like versions, node roles and other values can be defined
* tasks/main.yml: This is the primary play for the given playbook
* templates/main.yml:  This is where the OpenShift templates for a given play reside

Detailed runs of each playbook completed can be found [here](https://github.com/schmaustech/ansible-spx/blob/main/detailed-runs.md)
