BootStrap: docker
From: ubuntu:20.04

%post

	#TODO add blender to path somehow
	
    apt -y update
    apt -y install --no-install-recommends xz-utils wget git openmpi-bin mpi mpich
	apt clean

	# CONDA -------------------------
	wget -q --no-check-certificate https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
	bash Miniconda3-latest-Linux-x86_64.sh -b -p /conda
	rm Miniconda3-latest-Linux-x86_64.sh
	chmod -R 777 /conda

	# PYTHON LIBS -------------------------
	echo "Installing python libraries"
	/conda/bin/conda create -y -n blan1 python=3.7
	. /conda/etc/profile.d/conda.sh
	conda init
	conda activate blan1
	conda install -y python=3.7
	pip install --no-cache-dir tensorflow==2.2.0rc0 tensorflow_datasets pytest tables tblib
	conda install -y ipython pandas toolz matplotlib imageio click pyyaml bokeh mpi4py
	# conda clean --all -f -y
	
	echo ". /conda/etc/profile.d/conda.sh" >> $SINGULARITY_ENVIRONMENT
	echo "conda activate blan1" >> $SINGULARITY_ENVIRONMENT

	# BLENDER -------------------------
	wget -q --no-check-certificate https://mirror.clarkson.edu/blender/release/Blender2.82/blender-2.82a-linux64.tar.xz
    tar -xf /blender-2.82a-linux64.tar.xz
    rm /blender-2.82a-linux64.tar.xz
	/blender-2.82a-linux64/2.82/python/bin/python3.7m -m ensurepip
	/blender-2.82a-linux64/2.82/python/bin/pip3 install --upgrade pip
	/blender-2.82a-linux64/2.82/python/bin/pip3 install pyyaml
	chmod -R 777 /blender-2.82a-linux64
	
	
	SINGULARITYENV_PREPEND_PATH=/blender-2.82a-linux64
	

%environment
    export LC_ALL=C.UTF-8
    export LANG=C.UTF-8
	
%test
	echo blender -V
%labels
    Author DarikGamble
