# EKS-Ansible-CircleCI CI/CD Demo

This demonstrates the usage of CircleCI, Cloudformation, and Ansible to deploy a simple [hello-kubernetes](https://github.com/paulbouwer/hello-kubernetes) (Courtesy of [Paul Bouwer](https://github.com/paulbouwer)) to [Amazon EKS](https://aws.amazon.com/eks/).

## Links

- [Github Repo](https://github.com/CSamuelLents/ansible-eks-circleci)
- [Running application](http://aa00a411dc0c6433bb8ca4cbcac9a017-547059249.us-east-2.elb.amazonaws.com/)
- [Docker image](https://hub.docker.com/repository/docker/csamuellents/hello-kubernetes)

## Project Structure (abridged)

```text
.
├── .circleci
│   ├── ansible
│   │   ├── files
│   │   │   └── infrastructure.yml  # Cloudformation template
│   │   ├── hosts.ini               # Ansible hosts
│   │   ├── playbook.yml            # Main Ansible entrypoint
│   │   └── roles
│   │       ├── configure-server    # Install & configure dependencies
│   │       └── deployment          # K8s app deployment
│   └── config.yml                  # CircleCI config
├── Makefile                        # CI/CD helpers
├── Vagrantfile                     # VM config for local testing
├── app                             # hello-kubernetes app source
└── screenshots                     # CircleCI pipeline in action
```

## CI/CD

**Tasks Performed:**

1. Lint Dockerfile & JS
2. Build & upload Docker image
3. Deploy (or update) backend infrastructure
4. Deploy (or update) Kubernetes app
