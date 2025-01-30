# Intel® Data Center GPU Driver for OpenShift* 

## Overview
The Intel Data Center GPU Driver for OpenShift project focuses on the development, packaging, certification, and release of Intel® Data Center GPU driver container images for the [Red Hat OpenShift Container Platform (RHOCP)](https://www.redhat.com/en/technologies/cloud-computing/openshift/container-platform). This project allows users to leverage the pre-built driver container image to facilitate provisioning of Intel Data Center GPU cards on an OpenShift cluster. Furthermore, users can utilize the Intel Data Center GPU driver dockerfile provided by this project as a reference for constructing their own driver container images on-premises. Intel Data Center GPU driver container images for OpenShift are certified and published on the [Red Hat Container Catalog](https://catalog.redhat.com/software/containers/intel/intel-data-center-gpu-driver-container/6495ee55c8b2461e35fb8264).

The Intel Data Center GPU driver container image is built from the [Intel GPU Repository](https://github.com/intel-gpu). It includes:
- [Intel® Graphics Driver Backports for Linux* OS (i915) for Red Hat Enterprise Linux (RHEL)](https://github.com/intel-gpu/intel-gpu-i915-backports/tree/backport/main) with Intel® Converged Security Engine (Intel® CSE) and Intel® Platform Monitoring Technology (Intel® PMT) modules
- [Intel® GPU firmware](https://github.com/intel-gpu/intel-gpu-firmware)

## Install Intel Data Center GPU Driver on RHOCP
We recommend users use the [Kernel Module Management (KMM) operator](https://docs.openshift.com/container-platform/4.12/hardware_enablement/kmm-kernel-module-management.html) to install and manage the Intel Data Center GPU driver on RHOCP. The KMM operator can be used to deploy all the necessary driver components as well as the firmware from within the driver container image. 

To install Intel Data Center GPU drivers on OpenShift using the KMM operator, please follow [pre-build mode support](https://github.com/intel/intel-technology-enabling-for-openshift/tree/main/kmmo#deploy-intel-data-center-gpu-driver-with-pre-build-mode) from the [Intel Technology Enabling for OpenShift](https://github.com/intel/intel-technology-enabling-for-openshift). 

For users who prefer to create customized driver container images, the on-premises build mode is available as an option. This mode enables users to build and deploy their own container images on their OpenShift cluster.

## Upgrade Intel Data Center GPU Driver with RHOCP
Upgrading of the Intel Data Center GPU drivers are supported via two scenarios: 
- **Driver Upgrade Scenario**: This scenario is used when there is a new release from the Intel GPU Driver Repository. After the evaluation, a corresponding Intel Data Center GPU Driver container image will be built, certified, and published on the Red Hat Container Catalog. Users can make use of the KMM Operator to upgrade Intel data center GPU driver with RHOCP.  
**Notes:** The seamless upgrade feature is still under development in Kernel Module Management project.
- **Kernel Upgrade Scenario**: To ensure compatibility with each new Red Hat CoreOS (RHCOS) kernel used by RHOCP, the Intel GPU driver container images are re-built with the corresponding kernel version. This image is certified and then published on the Red Hat Container Catalog. KMM Operator can be used to deploy the driver container image matching the new RHCOS kernel version when upgrading the RHOCP cluster.

## Support
If users encounter any issues or have questions regarding Intel Data Center GPU Driver with RHOCP, we recommend them to seek support through the following channels:
### Commercial Support from Red Hat
This project facilitates provisioning pre-built Intel Data Center GPU drivers with [Intel Technology Enabling for OpenShift](https://github.com/intel/intel-technology-enabling-for-openshift) project, which are then certified and published in the Red Hat Container Catalog. Commercial RHOCP release support is outlined in the [Red Hat OpenShift Container Platform Life Cycle Policy](https://access.redhat.com/support/policy/updates/openshift) and Intel collaborates with Red Hat to address specific requirements from our users.
### Open-Source Community Support
Intel Data Center GPU Drivers for OpenShift is run as an open-source project on GitHub. Project GitHub [issues](https://github.com/intel/intel-data-center-gpu-driver-for-openshift/issues) related to pre-built and on-premises driver builds can be used as the primary support interface for users to submit feature requests and report issues to the community. Please provide detailed information about your issue and steps to reproduce it, if possible.

## Contribute
See [CONTRIBUTING](/CONTRIBUTING.md) for more information.

## License
Distributed under the open source license. See [LICENSE](/LICENSE.txt) for more information.

## Security
To report a potential security vulnerability, please refer to [security.md](/security.md) file.

## Code of Conduct
Intel has adopted the Contributor Covenant as the Code of Conduct for all of its open source projects. See [CODE_OF_CONDUCT](/CODE_OF_CONDUCT.md) file.
