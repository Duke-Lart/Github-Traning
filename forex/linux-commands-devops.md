# Linux Commands for DevOps Engineers

This document collects practical Linux commands that DevOps engineers use for daily operations, troubleshooting, deployment support, and system administration. Each command below includes what it does, when to use it, and an example.

## 1. `pwd`

**Purpose:** Shows the current working directory.

**Why it matters in DevOps:** When working on remote servers, CI runners, or containers, it is easy to lose track of where you are. `pwd` confirms your exact location before running commands that may affect files or services.

**Example:**

```bash
pwd
```

## 2. `ls`

**Purpose:** Lists files and directories.

**Why it matters in DevOps:** Useful for inspecting deployments, release directories, config locations, mounted volumes, and log folders.

**Common options:**
- `ls -l` for detailed view
- `ls -a` to include hidden files
- `ls -lh` for human-readable file sizes

**Example:**

```bash
ls -lah /etc/nginx
```

## 3. `cd`

**Purpose:** Changes the current directory.

**Why it matters in DevOps:** Required when navigating infrastructure directories, application paths, build outputs, or mounted container volumes.

**Example:**

```bash
cd /var/log
```

## 4. `mkdir`

**Purpose:** Creates directories.

**Why it matters in DevOps:** Used for preparing release folders, backup locations, mount points, and scripts directories.

**Example:**

```bash
mkdir -p /opt/apps/releases/2026-04-06
```

## 5. `cp`

**Purpose:** Copies files or directories.

**Why it matters in DevOps:** Frequently used for backups, duplicating configs, or promoting build artifacts.

**Example:**

```bash
cp -r /etc/nginx /etc/nginx.backup
```

## 6. `mv`

**Purpose:** Moves or renames files and directories.

**Why it matters in DevOps:** Useful for atomic deployments, rotating files, or renaming configuration files.

**Example:**

```bash
mv app.conf app.conf.bak
```

## 7. `rm`

**Purpose:** Removes files or directories.

**Why it matters in DevOps:** Helpful for cleanup, but dangerous. A DevOps engineer should use it carefully, especially with recursive flags.

**Common options:**
- `rm -f` force remove
- `rm -r` recursive remove
- `rm -rf` force recursive remove

**Example:**

```bash
rm -rf /tmp/old-build
```

## 8. `cat`

**Purpose:** Displays file contents.

**Why it matters in DevOps:** Fast way to inspect config files, environment files, shell scripts, and service definitions.

**Example:**

```bash
cat /etc/hosts
```

## 9. `less`

**Purpose:** Opens files for scrollable reading.

**Why it matters in DevOps:** Better than `cat` for large logs and long config files.

**Example:**

```bash
less /var/log/syslog
```

## 10. `tail`

**Purpose:** Shows the last lines of a file.

**Why it matters in DevOps:** Essential for live log monitoring during deployments and incident response.

**Common option:**
- `tail -f` follows new log output in real time

**Example:**

```bash
tail -f /var/log/nginx/access.log
```

## 11. `head`

**Purpose:** Shows the first lines of a file.

**Why it matters in DevOps:** Useful for validating file headers, CSVs, and generated reports.

**Example:**

```bash
head -20 /var/log/cloud-init.log
```

## 12. `grep`

**Purpose:** Searches for text patterns inside files.

**Why it matters in DevOps:** Used constantly to filter logs, inspect configs, find errors, and search code or manifests.

**Common options:**
- `grep -i` case-insensitive search
- `grep -r` recursive search
- `grep -n` show line numbers

**Example:**

```bash
grep -rin "error" /var/log
```

## 13. `find`

**Purpose:** Searches for files and directories.

**Why it matters in DevOps:** Useful for locating configs, logs, certificates, backups, or stale artifacts.

**Example:**

```bash
find /etc -name "*.conf"
```

## 14. `chmod`

**Purpose:** Changes file permissions.

**Why it matters in DevOps:** Important for scripts, SSH keys, deployment files, and security hardening.

**Example:**

```bash
chmod 600 ~/.ssh/id_rsa
```

## 15. `chown`

**Purpose:** Changes file ownership.

**Why it matters in DevOps:** Required when fixing permission issues for services, deployment users, and shared volumes.

**Example:**

```bash
chown -R www-data:www-data /var/www/app
```

## 16. `ps`

**Purpose:** Displays running processes.

**Why it matters in DevOps:** Helps identify application processes, zombie tasks, or stuck services.

**Example:**

```bash
ps aux | grep nginx
```

## 17. `top`

**Purpose:** Shows real-time system resource usage.

**Why it matters in DevOps:** Useful during outages and performance investigations to identify CPU and memory pressure.

**Example:**

```bash
top
```

## 18. `df`

**Purpose:** Displays disk space usage.

**Why it matters in DevOps:** Critical for monitoring servers and preventing downtime caused by full disks.

**Example:**

```bash
df -h
```

## 19. `du`

**Purpose:** Estimates file and directory sizes.

**Why it matters in DevOps:** Helps determine what is consuming space when a server starts filling up.

**Example:**

```bash
du -sh /var/log/*
```

## 20. `free`

**Purpose:** Shows memory and swap usage.

**Why it matters in DevOps:** Useful for diagnosing memory exhaustion and checking whether swap is being heavily used.

**Example:**

```bash
free -h
```

## 21. `uname`

**Purpose:** Displays system information.

**Why it matters in DevOps:** Helpful for validating kernel versions and platform details on servers or containers.

**Example:**

```bash
uname -a
```

## 22. `hostnamectl`

**Purpose:** Shows or sets hostname and system metadata.

**Why it matters in DevOps:** Useful for server identification and validation in fleet management.

**Example:**

```bash
hostnamectl
```

## 23. `ip`

**Purpose:** Shows and manages network settings.

**Why it matters in DevOps:** Preferred modern tool for checking interfaces, routes, and IP addresses during connectivity issues.

**Example:**

```bash
ip addr show
ip route
```

## 24. `ping`

**Purpose:** Tests network connectivity.

**Why it matters in DevOps:** Quick first step to confirm whether a host is reachable.

**Example:**

```bash
ping google.com
```

## 25. `curl`

**Purpose:** Sends HTTP requests from the command line.

**Why it matters in DevOps:** One of the most important commands for API testing, health checks, webhook debugging, and service verification.

**Example:**

```bash
curl -I https://example.com
curl -X GET https://api.example.com/health
```

## 26. `wget`

**Purpose:** Downloads files from the web.

**Why it matters in DevOps:** Useful for retrieving packages, installation scripts, assets, or test payloads on remote systems.

**Example:**

```bash
wget https://example.com/file.tar.gz
```

## 27. `ss`

**Purpose:** Displays socket and port information.

**Why it matters in DevOps:** Helps verify whether services are listening on expected ports and identify port conflicts.

**Example:**

```bash
ss -tulpn
```

## 28. `systemctl`

**Purpose:** Manages services on systems using `systemd`.

**Why it matters in DevOps:** Core command for starting, stopping, restarting, enabling, and checking application or infrastructure services.

**Example:**

```bash
systemctl status nginx
systemctl restart docker
systemctl enable nginx
```

## 29. `journalctl`

**Purpose:** Reads logs from `systemd` services.

**Why it matters in DevOps:** Extremely useful for debugging service failures and reviewing logs by unit, time, or boot.

**Example:**

```bash
journalctl -u nginx -f
```

## 30. `crontab`

**Purpose:** Manages scheduled jobs.

**Why it matters in DevOps:** Commonly used for automated backups, cleanup scripts, health checks, and periodic maintenance.

**Example:**

```bash
crontab -l
crontab -e
```

## 31. `tar`

**Purpose:** Archives and extracts files.

**Why it matters in DevOps:** Common for backups, build packaging, and log export.

**Example:**

```bash
tar -czf backup.tar.gz /etc/nginx
```

## 32. `scp`

**Purpose:** Securely copies files between systems over SSH.

**Why it matters in DevOps:** Useful for quick file transfers, config pushes, and backup retrieval when automation is not yet in place.

**Example:**

```bash
scp app.tar.gz user@server:/opt/apps/
```

## 33. `ssh`

**Purpose:** Connects to remote systems securely.

**Why it matters in DevOps:** One of the most fundamental commands for remote server access, troubleshooting, and administration.

**Example:**

```bash
ssh user@server
```

## 34. `rsync`

**Purpose:** Synchronizes files efficiently between locations.

**Why it matters in DevOps:** Excellent for deployments, backups, and mirroring directories with minimal transfer.

**Example:**

```bash
rsync -avz ./build/ user@server:/var/www/app/
```

## 35. `docker`

**Purpose:** Manages containers, images, networks, and volumes.

**Why it matters in DevOps:** Essential for container-based development, build pipelines, and runtime operations.

**Example:**

```bash
docker ps
docker logs -f my-container
docker exec -it my-container /bin/sh
```

## 36. `kubectl`

**Purpose:** Manages Kubernetes clusters.

**Why it matters in DevOps:** Central command for inspecting pods, deployments, services, logs, and cluster resources.

**Example:**

```bash
kubectl get pods -A
kubectl describe pod my-pod
kubectl logs -f my-pod
```

## 37. `tee`

**Purpose:** Writes command output to both screen and file.

**Why it matters in DevOps:** Useful when capturing logs or command results during troubleshooting while still viewing them live.

**Example:**

```bash
kubectl get pods -A | tee pods.txt
```

## 38. `xargs`

**Purpose:** Builds and executes commands from standard input.

**Why it matters in DevOps:** Helps automate bulk operations across files, pods, containers, or resources.

**Example:**

```bash
cat containers.txt | xargs -I {} docker logs {}
```

## 39. `env`

**Purpose:** Displays environment variables.

**Why it matters in DevOps:** Useful for verifying runtime configuration in shells, containers, and CI environments.

**Example:**

```bash
env | sort
```

## 40. `export`

**Purpose:** Sets environment variables in the current shell session.

**Why it matters in DevOps:** Common when testing apps locally, running scripts, or defining credentials and runtime flags.

**Example:**

```bash
export APP_ENV=production
```

## Best Practices for DevOps Engineers

- Verify your current directory with `pwd` before deleting or moving files.
- Prefer non-destructive inspection commands first, such as `ls`, `cat`, `less`, `grep`, and `find`.
- Be cautious with `rm -rf`, `chmod`, and `chown` on production systems.
- Use `tail -f`, `journalctl`, `top`, `free`, and `df -h` together during incident response.
- Learn `curl`, `ssh`, `systemctl`, `docker`, and `kubectl` deeply because they are used constantly in modern infrastructure work.
- Document one-off recovery commands before running them in production.

## Conclusion

A DevOps engineer uses Linux commands not just to navigate the system, but to observe state, diagnose failures, automate operations, and keep services reliable. Strong command-line skills improve troubleshooting speed, reduce mistakes, and support better automation practices.
