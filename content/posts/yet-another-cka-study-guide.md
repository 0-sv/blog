---
title: "Yet Another Cka Study Guide"
date: 2020-03-05T12:46:08+07:00
draft: false
---
As of March 2020 there are loads of resources to study for CKA (Certified Kubernetes Administrator). A lot of people have compiled their tips and tricks, created exercise repositories and applications, compiled yet more lists of additional resources, etc. 

I'd like to contribute by sharing my resource list. This is not my original work, and you will find all sources in the "Source index" paragraph. I've scheduled the test for next month and I'll report later to share my own opinion about the test, if there's anything I can contribute. This might be because of the upgrade from Kubernetes 1.16 to 1.17. 

## Exam Objectives (https://github.com/walidshaari/Kubernetes-Certified-Administrator)

These are the exam objectives you review and understand in order to pass the test.

[CNCF Exam Curriculum repository](https://github.com/cncf/curriculum/blob/master/CKA_Curriculum_V1.17.pdf)

### [Core Concepts](https://kubernetes.io/docs/concepts/) 19%

- [ ]  [Understand the Kubernetes API primitives](https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.16/)
    - [ ]  [concepts: Kubernetes Objects](https://kubernetes.io/docs/concepts/overview/working-with-objects/kubernetes-objects/)
    - [ ]  youtube: [Kubernetes Webinar Series - Kubernetes Architecture 101](https://www.youtube.com/watch?v=zeS6OyDoy78)
- [ ]  [Understand the Kubernetes cluster architecture](https://kubernetes.io/docs/concepts/overview/components/)
    - [ ]  youtube: [A Technical Overview of Kubernetes (CoreOS Fest 2015) by Brendan Burns](https://www.youtube.com/watch?v=WwBdNXt6wO4)
        - *Coupled applications is like driving a truck with a hangar (visualize it)*
        - *DevOps got the idea right but not the implementation: it's more like "application" ops since we now have four layers: hardware ops, kernel/os ops, cluster ops and application ops.*
        - *Idea of declarative state with simple primitives (CRUD), not a 'complex'  state machine.*
            - *Reconciliation loop*
- [ ]  [Understand Services and other network primitives](https://kubernetes.io/docs/concepts/services-networking/service/)
    - [ ]  youtube: [Life of a Packet [I] - Michael Rubin, Google](https://www.youtube.com/watch?v=0Omvgd7Hg1I)
    - [ ]  youtube: [The ins and outs of networking in Google Container Engine and Kubernetes (Google Cloud Next '17)](https://www.youtube.com/watch?v=y2bhV81MfKQ)

### [Installation, Configuration and Validation](https://github.com/kelseyhightower/kubernetes-the-hard-way/tree/f9486b081f8f54dd63a891463f0b0e783d084307) 12%

- [ ]  Design a Kubernetes cluster
- [ ]  [Install Kubernetes masters and nodes, including the use of TLS bootstrapping](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/install-kubeadm/)
- [ ]  [Configure secure cluster communications](https://kubernetes.io/docs/tasks/tls/managing-tls-in-a-cluster/)
- [ ]  [Configure a Highly-Available Kubernetes cluster](https://kubernetes.io/docs/admin/high-availability/)
- [ ]  [Know where to get the Kubernetes release binaries](https://kubernetes.io/docs/getting-started-guides/binary_release/#prebuilt-binary-release)
- [ ]  [Provision underlying infrastructure to deploy a Kubernetes cluster](https://github.com/kelseyhightower/kubernetes-the-hard-way/blob/f9486b081f8f54dd63a891463f0b0e783d084307/docs/01-infrastructure-gcp.md)
- [ ]  [Choose a network solution](https://kubernetes.io/docs/concepts/cluster-administration/networking/)
- [ ]  Choose your Kubernetes infrastructure configuration
- [ ]  Run end-to-end tests on your cluster
    - Some simple commands will cover most cases:

        $ kubectl cluster-info
        $ kubectl get nodes
        $ kubectl get componentstatuses
        $ kubectl get pods -o wide --show-labels --all-namespaces
        $ kubectl get svc  -o wide --show-labels --all-namespaces

- [ ]  For more advanced end to end testing, which may not be covered on the exam, also see:
    - [End-To-End Testing in Kubernetes](https://github.com/kubernetes/community/blob/master/contributors/devel/sig-testing/e2e-tests.md)
    - [Using CNCF k8s conformance](https://github.com/cncf/k8s-conformance/blob/master/instructions.md)
    - [Heptio Sonobuoy Scanner](https://scanner.heptio.com/)

### Security 12%

- [ ]  [Securing a kubernetes cluster](https://kubernetes.io/docs/tasks/administer-cluster/securing-a-cluster/)
    - [ ]  youtube: [Building for Trust: How to Secure Your Kubernetes Cluster [I] - Alexander Mohr & Jess Frazelle](https://www.youtube.com/watch?v=YRR-kZub0cA)
- [ ]  [Know how to configure authentication and authorization](https://kubernetes.io/docs/admin/authorization/rbac/)
    - [ ]  [Access the api](https://kubernetes.io/docs/admin/accessing-the-api/)
    - [ ]  [Authentication](https://kubernetes.io/docs/reference/access-authn-authz/authentication/)
    - [ ]  [Authorization with RBAC](https://kubernetes.io/docs/admin/authorization/rbac/)
    - [ ]  [Admission Control](https://kubernetes.io/docs/admin/admission-controllers/)
- [ ]  [Understand Kubernetes security primitives]
    - [ ]  [Pod Security Policy](https://kubernetes.io/docs/concepts/policy/pod-security-policy/)
        - [ ]  [PSP and RBAC](https://github.com/kubernetes/examples/blob/master/staging/podsecuritypolicy/rbac/README.md)
- [ ]  [Know to configure network policies](https://kubernetes.io/docs/tasks/administer-cluster/declare-network-policy/)
    - [ ]  [Blog: Kubernetes network policy](https://ahmet.im/blog/kubernetes-network-policy/)
    - [ ]  [Katacoda Calico](https://www.katacoda.com/projectcalico/scenarios/calico)
- [ ]  [Create and manage TLS certificates for cluster components](https://kubernetes.io/docs/tasks/tls/managing-tls-in-a-cluster/)
- [ ]  Work with images securely
- [ ]  [Define security contexts](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/)
- [ ]  [Secure persistent key value store](https://kubernetes.io/docs/concepts/configuration/secret/)
- [ ]  Work with role-based access control

### [Networking](https://kubernetes.io/docs/concepts/cluster-administration/networking/) 11%

- [ ]  [Understand the networking configuration on the cluster nodes](https://kubernetes.io/docs/concepts/cluster-administration/networking/)
- [ ]  Understand Pod networking concepts
    - [ ]  youtube: [The ins and outs of networking in Google Container Engine and Kubernetes (Google Cloud Next '17)](https://www.youtube.com/watch?v=y2bhV81MfKQ)
    - [ ]  youtube: [Networking with Kubernetes](https://www.youtube.com/watch?v=WwQ62OyCNz4)
    - [ ]  [Illustrated Guide To Kubernetes Networking by Tim Hockin](https://speakerdeck.com/thockin/illustrated-guide-to-kubernetes-networking)
- [ ]  Understand service networking
    - [ ]  youtube: [Life of a Packet [I] - Michael Rubin, Google](https://www.youtube.com/watch?v=0Omvgd7Hg1I)
- [ ]  [Deploy and configure network load balancer](https://kubernetes.io/docs/tasks/access-application-cluster/create-external-load-balancer/)
- [ ]  [Know how to use Ingress rules](https://kubernetes.io/docs/concepts/services-networking/ingress/)
- [ ]  [Know how to configure and use the cluster DNS](https://kubernetes.io/docs/concepts/services-networking/dns-pod-service/)
- [ ]  [Understand CNI](https://github.com/containernetworking/cni)
    - [ ]  [More information on CNI](http://www.dasblinkenlichten.com/understanding-cni-container-networking-interface/)

### Cluster Maintenance 11%

- [ ]  [Understand Kubernetes cluster upgrade process](https://kubernetes.io/docs/getting-started-guides/ubuntu/upgrades/)
    - [ ]  Best resource upgrade is to watch [TGI Kubernetes 011: Upgrading to 1.8 with kubeadm](https://youtu.be/x9doB5eJWgQ)
- [ ]  [Facilitate operating system upgrades](https://cloud.google.com/container-engine/docs/clusters/upgrade) #need review to make it more platform agnostic
- [ ]  [Implement backup and restore methodologies](https://kubernetes.io/docs/getting-started-guides/ubuntu/backups/)
- [ ]  [Etcd management/backups/restore](https://kubernetes.io/docs/tasks/administer-cluster/configure-upgrade-etcd)

### [Troubleshooting](https://kubernetes.io/docs/tasks/debug-application-cluster/troubleshooting/) 10%

- [ ]  [Troubleshoot application failure](https://kubernetes.io/docs/tasks/debug-application-cluster/determine-reason-pod-failure/)
    - [ ]  [Application Introspection and Debugging](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-application-introspection/)
    - [ ]  [Services](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-service/)
- [ ]  [Troubleshoot control plane failure](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-cluster/)
    - [ ]  youtube [Kubernetes Day 2: Cluster Operations [I] - Brandon Philips, CoreOS](https://www.youtube.com/watch?v=U1zR0eDQRYQ)
    - [ ]  Safaribooksonline: [https://www.safaribooksonline.com/library/view/oscon-2016-video/9781491965153/video246982.html](https://www.safaribooksonline.com/library/view/oscon-2016-video/9781491965153/video246982.html)
- [ ]  [Troubleshoot worker node failure](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-cluster/)
- [ ]  Troubleshoot networking

### [Storage](https://kubernetes.io/docs/concepts/storage/volumes/) 7%

- [ ]  [Understand persistent volumes and know how to create them](https://kubernetes.io/docs/concepts/storage/persistent-volumes/)
- [ ]  [Understand access modes for volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#access-modes)
- [ ]  [Understand persistent volume claims primitive](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims)
- [ ]  [Understand Kubernetes storage objects](https://kubernetes.io/docs/concepts/storage/volumes/#types-of-volumes)
- [ ]  [Know how to configure applications with persistent storage](https://kubernetes.io/docs/tasks/configure-pod-container/configure-volume-storage/)

### Application Lifecycle Management 8%

- [ ]  [Understand Deployments and how to perform rolling updates and rollbacks](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
- [ ]  [Know various ways to configure applications](https://kubernetes.io/docs/concepts/cluster-administration/manage-deployment/)
- [ ]  [Know how to scale applications](https://kubernetes.io/docs/concepts/cluster-administration/manage-deployment/#scaling-your-application)
- [ ]  Understand the primitives necessary to create a self-healing application

### Scheduling 5%

- [ ]  [Use label selectors to schedule Pods](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/)
- [ ]  [Understand the role of DaemonSets](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)
- [ ]  [Understand how resource limits can affect Pod scheduling](https://kubernetes.io/docs/tasks/administer-cluster/memory-default-namespace/)
- [ ]  [Understand how to run multiple schedulers and how to configure Pods to use them](https://kubernetes.io/docs/tasks/administer-cluster/configure-multiple-schedulers/)
- [ ]  [Manually schedule a pod without a scheduler](https://kubernetes.io/docs/tasks/administer-cluster/static-pod/)
If you require a pod to start on a specific node, you can specify this in POD spec.nodeName, that is what DaemonSets do.
- [ ]  [Display scheduler events](https://stackoverflow.com/questions/28857993/how-does-kubernetes-scheduler-work/28874577#28874577)
/var/log/kube-scheduler.log on the control/master node
or use `kubectl describe` as in
- [ ]  $kubectl describe pods <POD NAME UNDER Investigation>  | grep -A7 ^Events
- [ ]  [Know how to configure the Kubernetes scheduler](https://kubernetes.io/docs/tasks/administer-cluster/configure-multiple-schedulers/)

### [Logging/Monitoring](https://kubernetes.io/docs/concepts/cluster-administration/logging/) 5%

- [ ]  [Monitoring Kubernetes](https://www.datadoghq.com/blog/monitoring-kubernetes-era/)
- [ ]  [Understand how to monitor all cluster components](https://kubernetes.io/docs/tasks/debug-application-cluster/resource-usage-monitoring/)
- [ ]  [Pod and Node metrics](https://kubernetes.io/docs/reference/kubectl/cheatsheet/#interacting-with-running-pods)
- [ ]  Understand how to monitor applications
- [ ]  [Manage cluster component logs](https://kubernetes.io/docs/tasks/debug-application-cluster/debug-cluster/#looking-at-logs)
    - [ ]  Master
        - /var/log/kube-apiserver.log - API Server, responsible for serving the API
        - /var/log/kube-scheduler.log - Scheduler, responsible for making scheduling decisions
        - /var/log/kube-controller-manager.log - Controller that manages replication controllers
    - [ ]  Worker Nodes
        - /var/log/kubelet.log - Kubelet, responsible for running containers on the node
        - /var/log/kube-proxy.log - Kube Proxy, responsible for service load balancing
- [ ]  [Manage application logs](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#logs)

### Exercises

- [ ]  [https://linuxacademy.com/course/cloud-native-certified-kubernetes-administrator-cka/](https://linuxacademy.com/course/cloud-native-certified-kubernetes-administrator-cka/)
- [ ]  [https://github.com/David-VTUK/CKA-StudyGuide](https://github.com/David-VTUK/CKA-StudyGuide)
- [ ]  [https://github.com/ShubhamTatvamasi/kubernetes-practice-tests](https://github.com/ShubhamTatvamasi/kubernetes-practice-tests)
- [ ]  [http://devnetstack.com/certified-kubernetes-administrator-exam-study-guide/](http://devnetstack.com/certified-kubernetes-administrator-exam-study-guide/)
- [ ]  [https://github.com/kelseyhightower/kubernetes-the-hard-way](https://github.com/kelseyhightower/kubernetes-the-hard-way)
- [ ]  [https://github.com/arush-sal/cka-practice-environment](https://github.com/arush-sal/cka-practice-environment)

### Tips

- It’s 3 hours long
- 24 questions
- Pass mark is 74%
- Completely practical, no theory
- All on the command line
- You take the exam at home,
    - on your own computer.
- Clear your desk of everything
    - Drinks, books, pens, cuddly toys.
- You can have 2 browser tabs open
    1. The actual exam
    2. [The official Kubernetes docs](https://kubernetes.io/docs/) site
- Questions are visibly weighted
    - with a percentage
- The harder the question, the more points
- 

    source <(kubectl completion bash)

- 

    k = 'kubectl'
    kgp = 'kubectl get pods'
    kgs = 'kubectl get svc'
    kgc = 'kubectl get componentstatus'

- Start every question with an example from the docs and update it to answer your question
- Learn to create the Kubernetes objects FAST
- Have a small amount of knowledge of how to SysAdmin a Kubernetes cluster
- Use the docs site search functionality. A lot.
- Prioritise your questions
- Use the command line kubectl explain will help you during the exam.
- Carefully study the topic of
    - [Static Pods](https://kubernetes.io/docs/tasks/administer-cluster/static-pod/), this will help you very well when troubleshooting the non-working Kubernetes components.
    - [TLS Bootstrapping](https://kubernetes.io/docs/reference/command-line-tools-reference/kubelet-tls-bootstrapping/). From my point of view the most voluminous question on the exam. It seemed to me more difficult than Mumshad described in his course and in the practical tests.
- "If you don’t have specific knowledge about container tecnologies and docker, read the O’Reilly’s book “[Docker: Up & Running](http://shop.oreilly.com/product/0636920036142.do)“, the exam doesn’t require specific knowledge about docker but, since Kubernetes is an orchestrator for containers, this is a needed base."
- "IMHO the best book about k8s is “**[Kubernetes in Action](https://www.manning.com/books/kubernetes-in-action)**” , it covers a lot of aspect about this software and it’s very detailed, you don’t need to read it from the beginning till the end, some chapters of the “part 3” are not required by the exam."

# Source index

- [Kubernauts resources list](https://docs.google.com/spreadsheets/d/10NltoF_6y3mBwUzQ4bcQLQfCE1BWSgUDcJXy-Qp2JEU/edit#gid=0)
- [kubernetes.io](http://kubernetes.io) ("Ensure you have the right version of Kubernetes documentation selected (e.g. v1.16 as of 20th Nov. 2019 exam) especially for API objects and annotations. This release removes several deprecated API's.")