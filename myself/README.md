export ns=default
alias k='kubectl -n $ns' # This helps when namespace in question doesn't have a friendly name 
alias kdr= 'kubectl -n $ns -o yaml --dry-run'.  # run commands in dry run mode and generate yaml.

vim ~/.vimrc
set nu
set expandtab
set shiftwidth=2
set tabstop=2

https://www.linkedin.com/pulse/my-ckad-exam-experience-atharva-chauthaiwale/
https://medium.com/@harioverhere/ckad-certified-kubernetes-application-developer-my-journey-3afb0901014
https://github.com/lucassha/CKAD-resources

Useful comments:
kubectl get po --show-labels