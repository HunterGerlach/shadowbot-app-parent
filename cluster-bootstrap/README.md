oc apply -f sa.yaml
oc apply -f role.yaml
oc apply -f rolebinding.yaml

oc create token -n <namespace> github-deployer

Get cluster URL (format: https://api.cluster-kfg9t.dynamic.opentlc.com:6443)
oc status
