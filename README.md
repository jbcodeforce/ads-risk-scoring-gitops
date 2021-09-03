# Automation Decision Service Risk Scoring demo gitops

This GitOps repository defines the deployment of a simple risk scoring solution which includes

* A Quarkus app to enter loan value, and is a client of the decision service
* A ADS decision service to score the loan risk

## How this was set up

* This GitOps repository was created with [KAM](https://github.com/redhat-developer/kam) with a command like

```sh
kam bootstrap \
--service-repo-url https://github.com/jbcodeforce/credit-origination-app \
--gitops-repo-url  https://github.com/jbcodeforce/ads-risk-scoring-gitops \
--image-repo quay.io/jbcodeforce/credit-origination-app \
--output ads-risk-scoring-gitops \
--prefix ads-risk-scoring --push-to-git=true \
--git-host-access-token <a-github-token> \
```

* Then from the credit-origination-app , we moved the service, deployment and  route declaration generated by the
Quarkus OpenShift plugin to the `environment/ads-risk-scoring-dev/apps/services/credit-origination-app/base/config` folder as

```
├── 100-deployment.yaml
├── 200-service.yaml
├── 300-route.yaml
└── kustomization.yaml
```

## Bootstrap the CI/CD
