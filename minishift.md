## Minishift
https://docs.okd.io/latest/minishift/getting-started/index.html

1. Download minishift binary (minishift.exe) and place it in PATH <br>
  PS C:\...> minishift<br>
  Minishift is a command-line tool that provisions and manages single-node OpenShift clusters optimized for development workflows.<br>

2. Create an external virtual switch in Hyper-V manager<br>

3. Configure virtual switch and vm-driver to use with minikube<br>
  PS C:\...> minishift config set hyperv-virtual-switch "ExtVSwitch"<br>
  PS C:\...> minishift config  set vm-driver hyperv<br>
    No Minishift instance exists. New 'vm-driver' setting will be applied on next 'minishift start'<br>
  
4. Start minishift cluster<br>
  PS C:\....> minishift start<br>
  PS C:\Users\selvarasu.ramasamy> minishift.exe console<br>
    Opening the OpenShift Web console in the default browser...<br>
  PS C:\Users\selvarasu.ramasamy> minishift stop<br>
    Stopping the OpenShift cluster...<br>
    Cluster stopped.<br>
