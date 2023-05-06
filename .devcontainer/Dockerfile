FROM mcr.microsoft.com/devcontainers/python:3.10

RUN python -m pip install --no-cache-dir --upgrade pip \
    && python -m pip install --no-cache-dir 'flit>=3.8.0' \
    && pip install --no-cache-dir --extra-index-url https://download.pytorch.org/whl/cu118 'torch>=2.0.0' \
    && pip install --no-cache-dir --find-links https://data.pyg.org/whl/torch-2.0.0+cu118.html torch_geometric pyg_lib torch_scatter torch_sparse

ENV FLIT_ROOT_INSTALL=1

COPY pyproject.toml .
RUN touch README.md \
    && mkdir -p src/gel \
    && python -m flit install --only-deps --deps production --extras all \
    && rm -r pyproject.toml README.md src
