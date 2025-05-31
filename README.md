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

## Authentication, Authorization,	and	Admission Control. 
1.	Navigate	to	the	directory	app-a/ch06/rbac-aggregation	of	the	checkedout	GitHub	repository	bmuschko/cka-study-guide.  
Create	a	ClusterRole	with	the	name	service-view	to	the	API resources	services	with	the	operations	get	and	list.	Create	the RoleBinding	named	ellasmith-service-view	in	the development	namespace.	Map	the	user	ellasmith	to	the ClusterRole	service-view.
Create	a	ClusterRole	with	the	name	combined.	Aggregate	cluster roles	based	on	the	matching	label	key-value	pair rbac.cka.cncf.com/aggregate:	"true".	Render	the selected	rules	of	the	ClusterRole	combined.	How	many	rules	do	you see?
Create	a	ClusterRole	with	the	name	deployment-modify	to	the API	resources	deployments	with	the	operations	create,	delete, patch,	and	update.	Assign	the	label	key-value	pair rbac.cka.cncf.com/aggregate:	"true".	Render	the selected	rules	of	the	ClusterRole	combined.	How	many	rules	do	you see?  
Run	a	command	to	figure	out	if	the	user	ellasmith	can	list	Services in	the	namespace	development.	Write	the	output	of	the	command	to the	file	list-services-ellasmith.txt.	The	output	is	either	“no”	or	“yes.”  
Run	a	command	to	figure	out	if	the	user	ellasmith	can	watch Deployments	in	the	namespace	production.	Write	the	output	of	the command	to	the	file	watch-deployments-ellasmith.txt.	The	output	is either	“no”	or	“yes.”  
2.	Create	the	ServiceAccount	named	api-access	in	a	new	namespace called	apps.  
Create	a	ClusterRole	with	the	name	api-clusterrole,	and	create	a ClusterRoleBinding	named	api-clusterrolebinding.	Map	the ServiceAccount	from	the	previous	step	to	the	API	resources	pods	with the	operations	watch,	list,	and	get.
Create	a	Pod	named	operator	with	the	image	nginx:1.21.1	in the	namespace	apps.	Expose	the	container	port	80.	Assign	the ServiceAccount	api-access	to	the	Pod.	Create	another	Pod	named disposable	with	the	image	nginx:1.21.1	in	the	namespace	rm. Do	not	assign	the	ServiceAccount	to	the	Pod.
Open	an	interactive	shell	to	the	Pod	named	operator.	Use	the command-line	tool	curl	to	make	an	API	call	to	list	the	Pods	in	the namespace	rm.	What	response	do	you	expect?	Use	the	command-line tool	curl	to	make	an	API	call	to	delete	the	Pod	disposable	in	the namespace	rm.	Does	the	response	differ	from	the	first	call?	You	can find	information	about	how	to	interact	with	Pods	using	the	API	via HTTP	in	the	reference	guide.





