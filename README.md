# Configure-SoftRoCE-on-Ubuntu

## Install user space dependencies

`Sudo apt-get install libibverbs1`
`Sudo apt-get install libibverbs-dev`
`Sudo apt-get install librdmacm1`
`Sudo apt-get install librdmacm-dev`
`Sudo apt-get install rdmacm-utils`
`Sudo apt-get install rdma-core`\

## Install Kernel space dependencies

RDMA Kernel modules are upstreamed in recent Ubuntu versions. However the modules need to be manually loaded.

`Sudo modprobe ib_uverbs`
`Sudo modprobe ib_cm`
`Sudo modprobe ib_core`
`Sudo modprobe ib_umad`
`Sudo modprobe rdma_cm`
`Sudo modprobe rdma_ucm`

And modules for ULPs as well
`Sudo modprobe ib_ipoib`
`Sudo modprobe ib_iser`
`Sudo modprobe ib_isert`

## Configure SoftRoCE
RoCE can be implemented both in the hardware and in the software. Soft-RoCE is the software implementation of the RDMA transport. Soft RoCE configuration requires user space driver which is merged in rdma-core package. To start, stop and configure SoftRoCE use `rxe_cfg` utility.\
First `rxe_cfg` needs to be used to load `rdma_rxe` driver as follows:\
`Sudo rxe_cfg start`

Once rxe driver is loaded, it needs to bind to Ethernet interface which is active and up and has a valid IP settings. e.g.\
`Sudo rxe_cfg add eno1`
 
Similarly to unload rxe driver,\
`Sudo rxe_cfg stop`


