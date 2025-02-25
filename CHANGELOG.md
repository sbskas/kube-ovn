# CHANGELOG

## v0.8.0 -- 2019/10/08

### Gateway
* Support active-backup mode centralized gateway high available

### Diagnose Tools
* Kubectl plugin to trace/tcpdump/diagnose pod network traffic
* Pinger to test cluster network quality and expose metrics to Prometheus

### IPAM
* Join subnet ip now can be displayed by `kubectl get ip`

### Security
* Enable port security to prevent Mac and IP spoofing
* Allow nodes to pods traffic for private subnet

### Mics
* Support hostport
* Update OVN/OVS to 2.11.3
* Update Go to 1.13 

## v0.7.0 -- 2019/08/21

### IPAM
* Reserve vNic for statefulset pods, statefulset pod will reuse previous nic info during statefulset lifetime
* New IP CRD, now you can use `kubectl get ip` to obtain ip allocation info

### Subnet
* Check logical switch existence before related operations
* Calculate default values for custom subnet
* Auto unbind previous subnet when namespace bind to a new subnet
* Subnet CRD now has status field to show ip allocation statistic and subnet condition
* Write subnet annotations back to bind namespace

### Security
* Enable traffic mirror by default
* Support select all type NetworkPolicy rules
* Private subnet now applies acl to all ports not only gateway ports

### IPv6
* Control plan components now can communicate with IPv6 protocol

### Misc
* New logo
* [中文文档](https://github.com/alauda/kube-ovn/wiki)
* Test Kube-OVN compatible on CentOS 7.5/Ubuntu 16.04 and Ubuntu 18.04
* Add support for Kubespray and kubeasz installation tools
* Rename cni conf to `00-kube-ovn.conflist` to improve kubelet priority
* Basic TCP [performance test](https://github.com/alauda/kube-ovn/wiki/%E9%98%BF%E9%87%8C%E4%BA%91%E6%B5%8B%E8%AF%95) on aliyun.

## v0.6.0 -- 2019/07/22
### Features
* Support traffic mirror
* Use webhook to check ip conflict
* Beta IPv6 support
* Use subnet CRD to replace namespace annotation
* Use go mod to manage dependency

### Bug fixes
* Remove RBAC dependency on cluster-admin
* Use kubernetes nodename to replace hostname

## v0.5.0 -- 2019/06/06
### Features
* Support NetworkPolicy by OVN ACL
* User can choose interface for inter-host communication
* User can set mtu of pod interface
* Set kernel args when start cniserver
* Add pprof and use it as liveness/readiness probe
* Assign default gw for default switch and node switch
* Expose more cmd args to configure controller and daemon

### Misc
* Remove mask field from ip annotation

## v0.4.1 -- 2019/05/27
This is a bugfix version

### Bug Fixes
* manual static ip allocation and automatic allocation should use different ip validation
* json: cannot unmarshal string into Go value of type request.PodResponse
* use ovsdb-client to get leader info to avoid log rotation
* use default-gw as default-exclude-ips and expose args to docs
* to cleanup all created resources, not only kube-ovn namespace.

## v0.4.0 -- 2019/05/16
### Features
* ovndb now support cluster ha mode
* kube-ovn-controller now support ha mode by leader election
* Pod IP can be exposed to external network directly
* Update OVN to 2.11.1 to fix some known bugs
* Parallelize kube-ovn process to improve control plane performance
* Add vagrant files to do e2e tests
* Use ovs-ctl and ovn-ctl to do health check
### Bug Fixes
* Check subnet cidr conflict
* Validate namespace and pod annotations
* Daemon wait for node annotations ready
* Reuse node annotations when kube-ovn-controller restart

## v0.3.0 -- 2019/04/19
### Features
* Namespaced Gateway for external connectivity
* Daemon ovn-nbctl to improve performance
### Fix
* Daemon init node gw before running controller
* Activate node switch by ping
* Fix ovn-nbctl daemon output format bugs
* ACL allow error

## v0.2.0 -- 2019/04/15
### Features
* Distributed Gateway for external connectivity
* Dynamic QoS for pod ingress/egress bandwidth
* Subnet isolation
### Bug Fixes
* Delete empty lb to improve performance
* Delete lb at node switch
* Delete ovn embedded dns
* Fix ovn restart failed issue


## v0.1.0 -- 2019/03/12
### Features
* IP/Mac automatic allocation
* IP/Mac static allocation
* Namespace bind subnet
* Namespaces share subnet
* Connectivity between node and pod 
### Issues
* Pod can not access external network
* No HA for control plan
