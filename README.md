# birdhouse-deploy-ouranos
Ouranos specific override.

We want to source control all configs to follow infrastructure-as-code in order
to achieve traceability and reproducibility.

Integration with [birdhouse-deploy](https://github.com/bird-house/birdhouse-deploy) repo:

* This repo should be checkout along side of `birdhouse-repo` repo:

```
.
├── birdhouse-deploy
│   └── birdhouse
│       └── env.local
│       └── docker-compose.yml
│       └── pavics-compose.sh
│       └── (...)
├── birdhouse-deploy-ouranos
│   └── ouranos-config
│       └── docker-compose-extra.yml
│       └── (...)
```

* This repo must be enabled in `birdhouse-deploy/birdhouse/env.local` file:

```
# Enable extra config override from this birdhouse-deploy-ouranos repo.
export EXTRA_CONF_DIRS="$EXTRA_CONF_DIRS /<absolute path to checkout>/birdhouse-deploy-ouranos/ouranos-config"

# Enable autodeploy of this birdhouse-deploy-ouranos repo for future update to this repo.
# Require the scheduler component of birdhouse-deploy to be enabled in EXTRA_CONF_DIRS.
export AUTODEPLOY_EXTRA_REPOS="$AUTODEPLOY_EXTRA_REPOS /<absolute path to checkout>/birdhouse-deploy-ouranos"
```
