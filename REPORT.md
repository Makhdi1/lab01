# Laba 01

## Project Development Utilities

### Environment Setup

export GITHUB_USERNAME=Makhdi1
export GIST_TOKEN=<token>
alias edit=subl


### Directory Structure


mkdir -p Makhdi1/workspace
cd Makhdi1/workspace
pwd
/home/user/Makhdi1/workspace

cd ..
pwd
/home/user/Makhdi1


mkdir -p workspace/tasks/
mkdir -p workspace/projects/
mkdir -p workspace/reports/
cd workspace



### Node.js Installation

wget https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz
tar -xf node-v6.11.5-linux-x64.tar.xz
rm -rf node-v6.11.5-linux-x64.tar.xz
mv node-v6.11.5-linux-x64 node

ls node/bin
node npm npx

echo ${PATH}
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

export PATH=${PATH}:pwd/node/bin
echo ${PATH}
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/home/user/Makhdi1/workspace/node/bin


### Activation Script

mkdir scripts
cat > scripts/activate<<EOF
export PATH=${PATH}:pwd/node/bin
EOF
source scripts/activate


### Gist Setup

gem install gist
Successfully installed gist-5.0.0
