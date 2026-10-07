# Docker-Inkscape

This file is part of the Docker-Inkscape project:
https://github.com/cyber-g/Docker-Inkscape

Alpine 3.24 image with Inkscape, and a small font collection, including Microsoft core fonts and fonts extracted from PowerPoint Viewer.

Build the image:

```sh
docker build -t inkscape .
```

Start an interactive shell in the current directory:

```sh
docker run --rm -it -v "$PWD:/work" inkscape
```

Export `drawing.svg` to PDF:

```sh
docker run --rm -v "$PWD:/work" inkscape inkscape drawing.svg --export-filename=drawing.pdf
```

## Maintenance

In GitHub repository **Settings > Secrets and variables > Actions**, add the secrets `DOCKERHUB_USERNAME` and `DOCKERHUB_TOKEN`, plus the variable `DOCKERHUB_IMAGE` (for example, `your-dockerhub-user/inkscape`).

To rotate an expiring token, create a replacement with read/write access in Docker Hub **Account Settings > Personal access tokens**, update GitHub's `DOCKERHUB_TOKEN` secret, then revoke the old token.

After changing the Dockerfile, commit and push to `main`; GitHub Actions builds and publishes the `latest` image. To publish a version, push a tag such as `v1.0.0`. Pull requests build the image without publishing it.
