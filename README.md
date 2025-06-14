[![Image on Docker Hub](https://github.com/GiantMolecularCloud/streamlit-base/actions/workflows/build-image.yml/badge.svg)](https://github.com/GiantMolecularCloud/streamlit-base/actions/workflows/build-image.yml)

# Streamlit Base

A base image intended to run [Streamlit](https://streamlit.io/) applications with [Poetry](https://python-poetry.org/) as the package manager.

The container expects a Poetry Python project mounted to `/app`, installs the required dependencies and runs entrypoint `/app/src/run.py` in Streamlit.
This setup allows to quickly test Streamlit applications and to modify them in-place.

To run this container, mount your Streamlit application code to `/app` and map the port your application uses.
```
docker run -it --rm  -v /path/to/streamlit/applciation:/app:ro -p 8501:8501 streamlit-base
```

Poetry is instructed to not create the venv in the project, so the mounted code stays clean.
This can also be enforced with a read-only mount (`-v host:container:ro`).
