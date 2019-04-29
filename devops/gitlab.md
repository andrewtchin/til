# Gitlab

## Setup Runner

Install `gitlab-runner` https://docs.gitlab.com/runner/install/linux-repository.html

Install `docker`
```
curl -fsSL get.docker.com -o get-docker.sh
sh get-docker.sh
```

Privileged runners need
```
sudo usermod -aG docker gitlab-runner
```

Register runner

- https://docs.gitlab.com/runner/register/
- https://docs.gitlab.com/ee/ci/docker/using_docker_build.html
- https://docs.gitlab.com/runner/commands

Register dind runner
```
sudo gitlab-runner register -n \
  --url https://gitlab.com/ \
  --registration-token TOKEN \
  --executor docker \
  --docker-image "docker:stable" \
  --docker-privileged \
  --tag-list dind \
  --docker-volumes /var/run/docker.sock:/var/run/docker.sock \
  --name gitlab-runner-1
```

Gitlab runner config
```
/etc/gitlab-runner/config.toml
```

## Other admin actions

Unregister runner
```
sudo gitlab-runner unregister -n gitlab-runner-1
```

## NFS Mount
```bash
sudo apt-get install nfs-common
```

Add mount to `/etc/fstab`
```bash
nfs.example.com:/widgets    /build/widgets    nfs    auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0
```

Add volume to `/etc/gitlab-runner/config.toml`
```bash
volumes = ["/cache", "/build/widgets:/build/widgets:ro"]
```

```bash
sudo gitlab-runner restart
```

## Periodic Cleanup

Put `runner-cleanup.sh` in `/etc/cron.weekly`

```bash
#!/bin/sh

# https://gitlab.com/gitlab-org/gitlab-runner/issues/2980
/usr/share/gitlab-runner/clear-docker-cache
docker rmi $(docker images -a --filter=dangling=true -q)
```
```
chmod 0755 runner-cleanup.sh
```
