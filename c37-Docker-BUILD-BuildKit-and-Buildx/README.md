# Learn with BuildKit (builder) and Buildx (client-side CLI)

---

## Step 1: Introduction

**BuildKit**: is an improved build engine for Docker, introduced to replace the legacy Docker builder.

It offers several improvements and new features, including:
- **Parallel**: BuildKit can run build steps in parallel, optimizing build times.
- **Caching**: BuildKit improves the use of cache by allowing you to cache individual build steps (layers) more effectively, which reduces rebuild times.
- **Incremental**: Only changed files are transferred between builds, reducing overhead.
- **Performance**: Overall, BuildKit provides better performance, storage management, and extensibility compared to the legacy builder


**Buildx**: is a Docker CLI plugin that extends the capabilities of Docker BuildKit.

It provides additional features such as:
- **Multi-Platform/Multi-Architecture**: Buildx allows you to build images for different platforms and architectures (e.g., amd64, arm64, etc.) from a single host.
- **Parallel**: Buildx supports parallel builds across multiple nodes, making it suitable for large-scale projects.

---

## Step 2: Docker Buildx Commands

```bash
# Show buildx version information
docker buildx version

# List builder instances
docker buildx ls

# Remove build cache
docker buildx prune

# Use default
docker buildx use --default default

# Create a new Buildx builder
docker buildx create --name mybuilder1 --driver docker-container --use

# Inspect Buildx builder
docker buildx inspect --builder mybuilder1

# Remove Buildx builder
docker buildx rm mybuilder1
```

---
