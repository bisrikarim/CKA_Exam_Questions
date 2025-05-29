# CKA_Exam_Questions
## Cluster	Installation using Kubeadm
![Screenshot_20250529_183234_Adobe Acrobat](https://github.com/user-attachments/assets/070d6899-99f3-4e7b-9d12-13835b4f7759)

1.	Create	a	cluster	with	four	nodes,	one	control	plane	node,	and	three worker	nodes.  
Create	a	Pod	named	nginx	that	uses	the	container	image nginx:1.27.4-alpine.  
Identify	the	node	the	Pod	has	been	scheduled	on.  
Evict	all	Pods	from	the	node	that	runs	the	Pod	at	once.	Do	not	use	the kubectl	delete	pod	command	to	perform	the	operation.	Ensure that	the	Pod	is	not	running	anymore.  
Prerequisite:	To	create	a	cluster	with	4	nodes	using	minikube,	run	the command	minikube	start	--nodes	4. 2.	Navigate	to	the	directory	app-a/ch04/upgrade-cluster-version	of	the checked-out	GitHub	repository	bmuschko/cka-study-guide.  
Start	up	the	VMs	running	the	cluster	using	the	command	vagrant up.	The	cluster	consists	of	a	single	control	plane	node	named	kubecontrol-plane,	and	one	worker	node	named	kube-worker-1. Open	an	interactive	shell	into	the	control	plane	node	and	inspect	the currently-used	Kubernetes	version	by	listing	all	the	nodes.  
Upgrade	all	nodes	of	the	cluster	from	Kubernetes	1.32.1	to	1.32.2.
![Screenshot_20250529_184945_Adobe Acrobat](https://github.com/user-attachments/assets/ca140fcd-5553-4024-be29-2870c8db6d17)

Once	done,	shut	down	the	cluster	using	vagrant	destroy	-f.

## Backing	Up	and Restoring	etcd
![Screenshot_20250529_182409_Adobe Acrobat](https://github.com/user-attachments/assets/0f0d0339-660f-48fa-95f1-93c1add91e01)  

1.	Navigate	to	the	directory	app-a/ch05/etcd-backup-restore	of	the checked-out	GitHub	repository	bmuschko/cka-study-guide.  
2.	Start	up	the VMs	running	the	cluster	using	the	command	vagrant	up.	The cluster	consists	of	a	single	control	plane	node	named	kubecontrol-plane,	and	one	worker	node	named	kube-worker-1.  
3.	Open	an	interactive	shell	into	the	control	plane	node	and	inspect	the currently-used	Kubernetes	version	by	listing	all	the	nodes.  
SSH	into	the	control	plane	node	host	machine.  
Identify	the	Pod	that runs	the	etcd	executable.  
Inspect	the	details	of	the	Pod	to	find	out	which version	of	etcd	it	is	running.  
Write	the	version	to	the	file	etcdversion.txt. Once	done,	shut	down	the	cluster	using	vagrant	destroy	-f.  
5.	Navigate	to	the	directory	app-a/ch05/etcd-backup-restore	of	the checked-out	GitHub	repository	bmuschko/cka-study-guide.  
6.	Start	up	the VMs	running	the	cluster	using	the	command	vagrant	up. The cluster	consists	of	a	single	control	plane	node	named	kubecontrol-plane,	and	one	worker	node	named	kube-worker-1.  
Open	an	interactive	shell	into	the	control	plane	node	and	inspect	the currently-used	Kubernetes	version	by	listing	all	the	nodes.  
The	etcdctl	and	etcdutl	tool	have	been	preinstalled	on	the	node kube-control-plane.  
Back	up	etcd	to	the	snapshot	file /opt/etcd.bak.  
Restore	etcd	from	the	snapshot	file.	Use	the	data directory	/var/bak.  
Once	done,	shut	down	the	cluster	using	vagrant	destroy	-f.
