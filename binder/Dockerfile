# Use the base image that already contains Jupyter Notebook
FROM jupyter/minimal-notebook

# Install GHC (Glasgow Haskell Compiler) and Cabal (Haskell build tool)
# Also, install libtinfo-dev which is required by GHC.
RUN apt-get update && apt-get install -y haskell-platform libtinfo-dev

# Update Cabal package list
RUN cabal update

# Install IHaskell (Haskell kernel for Jupyter)
# Cabal will download and install IHaskell along with its dependencies.
RUN cabal install ihaskell

# Install the IHaskell kernel into Jupyter
RUN ihaskell install

# Clean up unused package lists to reduce the image size
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Expose Jupyter notebook port (this is not strictly necessary for Binder, but a good practice)
EXPOSE 8888
