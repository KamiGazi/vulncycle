# Vulncycle

**Vulncycle** is an educational lab focused on the vulnerability lifecycle: detection - exploitation - patching - verification.

It provides instructions to use vulnerable applications, along with writeups on exploitation and patches demonstrating fixes.

Warning: This project does not guarantee the "complete" security of a given patch file. Patches here are only meant to handle the exploited vulnerability mentioned in the respective writeup, as this felt like the better approach for educational purposes.

---

## Dependencies
- [Docker](https://docs.docker.com/get-docker/)
- [DVWA (Damn Vulnerable Web Application)](https://github.com/digininja/DVWA)

---

## Getting Started

Clone this repo, then clone DVWA under `./lab-setup/`:

```bash
cd lab-setup
git clone https://github.com/digininja/DVWA.git
```

Start DVWA in Docker:

```bash
cd DVWA
docker compose up -d
```

The DVWA app will be available at: [http://localhost:4280](http://localhost:4280)

you can login with: 

```
Username: admin
Password: password
```

To shut down DVWA:

```bash
docker compose down
```

Refer to the [DVWA repository](https://github.com/digininja/DVWA) for more details on DVWA, though the app itself is pretty self-explanatory.

---

## Patched Mode

This repo contains patches for DVWA vulnerabilities. To test them, run DVWA with the override compose file:

```bash
cd lab-setup
docker compose -f DVWA/docker-compose.yml -f dvwa-patcher.override.yml up -d
```

Here you can attempt known exploits and confirm that the patched code prevents them.

Shut down the patched app:

```bash
docker compose -f DVWA/docker-compose.yml -f dvwa-patcher.override.yml down
```