# k8s_postgres_master_slave
PostgreSQL Master and Slave streaming replication using Kubernetes k8s

1. Create a diectory for master pg data
/data/pgsql/kube/master

2. Create a diectory for master pg data
/data/pgsql/kube/slave

3. Create 
	pv for master and slave
	pvc for master and slave
	service for master and slave
	statefulset for master and slave


	kubectl apply -f pv-master.yaml    # PV create for master
	kubectl apply -f pv-slave.yaml     # PV create for slave
	kubectl apply -f pv-pvc-master.yaml  # PVC create based on pv master
	kubectl apply -f pv-pvc-slave.yaml   # PVC create based on pv slave/standby/replica
	kubectl apply -f pg-master-service.yaml  # Service create for master
	kubectl apply -f pg-slave-service.yaml   # Service create for slave/standby/replica
	kubectl apply -f pg-master-statefulset.yaml  # Statefulset create for master 
	kubectl apply -f pg-master-statefulset.yaml  # Statefulset create for slave/standby/replica

4. Check using below commands 

	kubectl get pods # To check running pods
	kubectl get svc  # To check services
	kubectl get pv  # To check pv
	kubectl get pvc # To check pvc
	kubectl scale statefulset replicas=0 # To makes replcas to 0
	kubectl scale statefulset replicas=1 # To makes replicase to 1
	kubectl scale statefulset replicas=2 # To makes replicase to 2
