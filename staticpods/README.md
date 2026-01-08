# Static Pod Configuration Guide
# 
# Static pods are managed directly by kubelet, not the API server.
# They are useful for running critical system components like control plane pods.
#
# How to use Static Pods:
# 1. Copy the pod manifest to the kubelet's manifest directory:
#    Default path: /etc/kubernetes/manifests/
#    Or check kubelet config: staticPodPath in /etc/kubernetes/kubelet.conf
#
# 2. Kubelet automatically detects and creates the pod
#
# 3. Pod name will be: <pod-name>-<node-name>
#    Example: nginx-static-pod-master
#
# 4. To delete: Remove the manifest from the directory
#
# Characteristics of Static Pods:
# - Only run on specific node where manifest exists
# - Managed by kubelet, not API server scheduler
# - Cannot be deleted via kubectl delete pod
# - Useful for control plane components (apiserver, etcd, controller-manager, scheduler)
# - Appear in kubectl get pods with node name suffix
#
# Note: You cannot directly apply static pods with kubectl apply.
# You must copy the manifest file to the node's manifest directory.
