# fluxcd-example
Testing kustomize and fluxcd

export GITHUB_TOKEN=''

  flux bootstrap github \
  --token-auth \
  --owner=luismruizc \
  --repository=https://github.com/luismruizc/fluxcd-example \
  --branch=main \
  --path=clusters/fury-melikost-prometheus \
  --personal

flux reconcile helmrelease melikost-prometheus-adapter -n fury-melikost

flux uninstall --namespace=flux-system

flux install clusters/fury-melikost-prometheus
flux install clusters/fury-melikost-redis 

flux delete clusters/dev/cassandra

flux uninstall --namespace=flux-system


  flux bootstrap github \
  --token-auth \
  --owner=luismruizc \
  --repository=https://github.com/luismruizc/fluxcd-example \
  --branch=main \
  --path=clusters/prom+redis \
  --personal