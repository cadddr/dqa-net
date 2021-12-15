### download
replace s3 link with http://ai2-website.s3.amazonaws.com/data/ai2d-all.zip

### prepro without images
setup python 3.5.10 with pyenv (unneeded?) CFLAGS="-I$(brew --prefix openssl)/include -I$(brew --prefix bzip2)/include -I$(brew --prefix readline)/include -I$(xcrun --show-sdk-path)/usr/include" LDFLAGS="-L$(brew --prefix openssl)/lib -L$(brew --prefix readline)/lib -L$(brew --prefix zlib)/lib -L$(brew --prefix bzip2)/lib" pyenv install --patch 3.5.10 < <(curl -sSL github.com/python/cpython/commit/8ea6353.patch\?full_index\=1)
check out qa2hypo and stanford-corenlp-python (with jsonrpc)
add submodules to path - sys.path.append('qa2hypo/en'); sys.path.append('qa2hypo/en/wordnet')
use python2, install with pyenv
upgrade pip
install requirements and missing packages - simplejson-3.17.6 nltk to 3.0.0 
comment out extra loops in anno2rels, replace subtype with type_

### create fold
point to categories.json
save to data/s3/folds/fold23.json

### prepro with images
install torch - http://torch.ch/docs/getting-started.html
comment out cunn, cutorch imports, cuda references in lua script
protobuf - brew/conda install (didn't help?) export Protobuf_INCLUDE_DIR=/usr/local/Caskroom/miniconda/base/include/google/protobuf 
loadcaffe - install from rockspec https://github.com/szagoruyko/loadcaffe
hdf5 1.8, brew link hdf5@1.8, then luarocks install hdf5
re-download caffe model
libpng 14.12 - sudo install from source (use target darwin), link dlib
re-install image (necessary?)

### train
install tensorflow 0.12