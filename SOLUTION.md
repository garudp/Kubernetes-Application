The problems occured and solution for that:

ERROR: failed to create cluster: failed to list nodes: command "docker ps -a --filter label=io.x-k8s.kind.cluster=qa-cluster --format '{{.Names}}'" failed with error: exit status 1

Docker is not running - systemctl start docker

----------------
The connection to the server localhost:8080 was refused - did you specify the right host or port?

I solve this by copied the config file present in the root to the ec2-user/.kube/config
I can also perform this with root user but I choose to stay in this user

----------------
0/2 nodes are available: 1 node(s) didn't match Pod's node affinity .
kubelet  Error: ImagePullBackOf
Back-off pulling image "gcr.io/google-samples/microservices-demo/adservice:v0.3.1

For the hostname we have found that kubernetes.io/hostname was having wrong hostname and this we found by checking the syntax document and in the example we found that it should be server hostname ip-172-31-40-48.eu-central-1.compute.internal

For the Image in the adservice.yaml finally I figure out that version is not available in the repository so I change it to available one

For redis that scheduling failed error for Pod's node affinity resolve by adding correct name at nodeSelector that is qa-cluster-worker, kubectl get nodes --show-labels command help to check exact name
