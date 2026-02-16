# Cosign Container - CleanStart

**Cosign** is a tool from the Sigstore project for signing and verifying container images. The CleanStart Cosign image provides a production-ready, security-hardened container optimized for enterprise environments. Built on a minimal base OS with comprehensive security hardening, this image delivers reliable application execution with advanced security features.

**📌 CleanStart Foundation:** Security-hardened, minimal base OS designed for enterprise containerized environments.

**Image Path:** `ghcr.io/cleanstart-containers/cosign`

**Registry:** CleanStart Registry

---

## Overview

Cosign is a container signing and verification tool from the Sigstore project that provides cryptographic signing for container images and artifacts. It enables secure supply chain practices by allowing you to sign, verify, and attest container images. This CleanStart Cosign container is part of the CleanStart application suite, featuring enterprise-grade security hardening, automated vulnerability management, and compliance with industry standards.

---

## About CleanStart

CleanStart is a comprehensive container registry providing security-hardened, enterprise-ready container images. Our images are designed with security-first principles, featuring minimal attack surfaces, regular security updates, and compliance with industry standards.

### About CleanStart Images

CleanStart images are built on secure, minimal base operating systems and optimized for production environments. Each image undergoes rigorous security testing, vulnerability scanning, and compliance validation to ensure enterprise-grade security and reliability.

---

## Image
```
ghcr.io/cleanstart-containers/cosign:latest-dev
```

---

## Key Features

- **Security-First Design**: Built with minimal attack surfaces and security hardening
- **Enterprise Compliance**: Meets industry standards including FIPS, STIG, and CIS benchmarks
- **Regular Updates**: Automated security patches and vulnerability management
- **Multi-Architecture Support**: Available for AMD64 and ARM64 architectures
- **Production Ready**: Optimized for enterprise deployment and scaling
- **Comprehensive Documentation**: Detailed guides and best practices for each image
- Container image signing and verification
- Integration with Sigstore infrastructure
- Keyless signing support
- Attestation generation and verification

---

## Quick Start

### Pull Commands
```bash
docker pull ghcr.io/cleanstart-containers/cosign:latest
docker pull ghcr.io/cleanstart-containers/cosign:latest-dev
```

### Run Commands

Basic test:
```bash
docker run -it --name cosign-test ghcr.io/cleanstart-containers/cosign:latest-dev
```

Production deployment:
```bash
docker run -d --name cosign-prod \
  --read-only \
  --security-opt=no-new-privileges \
  --user 1000:1000 \
  ghcr.io/cleanstart-containers/cosign:latest
```

---

## Quick Commands

### Check Version
```bash
docker run --rm ghcr.io/cleanstart-containers/cosign:latest-dev version
```

### Generate Keys
```bash
docker run --rm -it \
  -v $(pwd):/workspace -w /workspace \
  ghcr.io/cleanstart-containers/cosign:latest-dev \
  generate-key-pair
```

### Sign Image
```bash
docker run --rm \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v $(pwd):/workspace -w /workspace \
  ghcr.io/cleanstart-containers/cosign:latest-dev sign --key cosign.key <registry>/<image>:tag
```

### Verify Signature
```bash
docker run --rm \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v $(pwd):/workspace -w /workspace \
  ghcr.io/cleanstart-containers/cosign:latest-dev verify --key cosign.pub <registry>/<image>:tag
```

---

## Important Notes

- ⚠️ **Images must be in a registry** (not local-only)
- 🔒 **Keep `cosign.key` secure** - never commit to git
- ✅ **Share `cosign.pub`** - safe to distribute
- 📝 **Login to registry first:** `docker login`

Please go through sample-project for more details.

---

## Architecture Support

CleanStart images support multiple architectures to ensure compatibility across different deployment environments:

- **AMD64**: Intel and AMD x86-64 processors
- **ARM64**: ARM-based processors including Apple Silicon and ARM servers

### Architecture-based Pull Commands
```bash
docker pull --platform linux/amd64 ghcr.io/cleanstart-containers/cosign:latest
docker pull --platform linux/arm64 ghcr.io/cleanstart-containers/cosign:latest
```

---

## Resources

- **Official Documentation:** https://docs.sigstore.dev/cosign/overview/
- **Cosign GitHub Repository:** https://github.com/sigstore/cosign
- **Provenance / SBOM / Signature:** https://images.cleanstart.com/images/cosign
- **Docker Hub:** https://hub.docker.com/r/cleanstart/cosign
- **CleanStart All Images:** https://images.cleanstart.com/images/cosign/details
- **CleanStart Community Images:** https://hub.docker.com/u/cleanstart

---

## Vulnerability Disclaimer

CleanStart offers Docker images that include third-party open-source libraries and packages maintained by independent contributors. While CleanStart maintains these images and applies industry-standard security practices, it cannot guarantee the security or integrity of upstream components beyond its control.

Users acknowledge and agree that open-source software may contain undiscovered vulnerabilities or introduce new risks through updates. CleanStart shall not be liable for security issues originating from third-party libraries, including but not limited to zero-day exploits, supply chain attacks, or contributor-introduced risks.

**Security remains a shared responsibility:** CleanStart provides updated images and guidance where possible, while users are responsible for evaluating deployments and implementing appropriate controls.
