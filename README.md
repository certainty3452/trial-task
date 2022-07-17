# the task

- Deployment of the application consisting of of nginx webserver that proxies requests based on the URL path:
  - /google requests should be proxied to google.com
  - /freshcells requests should be proxied to freshcells.de
  - all others requests respond with redirect 302 to amazon.com
  - permanently redirect all requests for the domain without www. to the same domain with www.
- The deployment has HPA based on average CPU load: CPU threshold is 30% from 1cpu, minimum 2 replicas and maximum 5 replicas
- On each successful deployment of the Helm chart the API endpoint https://www.freshcells.de/some/api has to be called
- Ingress controller is nginx (doesn't need to be installed, suppose we have it already)

In addition to the main points, some additional features were impleneted:
- [Check configmap hashsum](https://github.com/certainty3452/trial-task/blob/main/templates/deployment.yaml#L18) to pod recreating each time config was changed
- [HighAvailability.enabled switch](https://github.com/certainty3452/trial-task/blob/main/templates/deployment.yaml#L75) enables functional to schedule pods run evenly to each node.
