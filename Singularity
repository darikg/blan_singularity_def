BootStrap: docker
From: python:3.7

%post
    apt -y update
    apt -y install --no-install-recommends xz-utils blender wget openmpi-bin

    mkdir -p /blan

    # Untar the blender binary
    wget https://mirror.clarkson.edu/blender/release/Blender2.82/blender-2.82a-linux64.tar.xz
    tar -xvf /blender-2.82a-linux64.tar.xz -C /blan
    rm /blender-2.82a-linux64.tar.xz

    chmod -R 777 /blan

     # Update pip and install dependencies
    pip install --no-cache-dir \
        tensorflow==2.2.0rc0 ipython pandas toolz matplotlib imageio \
        click pyyaml tensorflow_datasets bokeh tables

%environment
    export LC_ALL=C.UTF-8
    export LANG=C.UTF-8

%labels
    Author DarikGamble