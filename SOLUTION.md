The problems occured and solution for that:

ERROR: failed to create cluster: failed to list nodes: command "docker ps -a --filter label=io.x-k8s.kind.cluster=qa-cluster --format '{{.Names}}'" failed with error: exit status 1

Docker is not running - systemctl start docker

----------------
The connection to the server localhost:8080 was refused - did you specify the right host or port?

I solve this by copied the config file present in the root to the ec2-user/.kube/config
I can also perform this with root user but I choose to stay in this user.
