# Install BlazingSQL for CUDA 10.0
conda install -y -c conda-forge -c defaults -c nvidia -c rapidsai -c blazingsql/label/cuda10.0 -c blazingsql blazingsql-calcite blazingsql-orchestrator blazingsql-ral blazingsql-python python=3.7 cudatoolkit=10.0

pip install flatbuffers && \
    pip install jupyterlab
	
