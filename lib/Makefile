# Don't use the --user flag for setup.py develop mode with virtualenv.
DEV_USER_FLAG=$(shell python -c "import sys; print('' if hasattr(sys, 'real_prefix') else '--user')")

.PHONY: default
default: dev

.PHONY: install
install:
	python setup.py install

.PHONY: ops
ops:
	# mkdir -p build && cd build && cmake -C ~/trinity/utils/setup/caffe2/detectron_cmake_config.cmake -DUSE_TENSORRT=False -DCUDA_ARCH_NAME=Pascal .. && make -j$(shell nproc)
	mkdir -p build && cd build && cmake .. && make -j$(shell nproc)

.PHONY: dev
dev:
	python setup.py develop $(DEV_USER_FLAG)

.PHONY: clean
clean:
	python setup.py develop --uninstall $(DEV_USER_FLAG)
	rm -rf build
