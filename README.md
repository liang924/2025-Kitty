# 2025-Kitty
Installation guide for QAI

## Step 1 – Install Required Packages

sudo add-apt-repository universe
sudo apt update

## Step 2 – Clone the OAI Repository

git clone https://gitlab.eurecom.fr/oai/openairinterface5g.git
cd openairinterface5g
git submodule update --init --recursive

## Step 3 – Build the Software

./cmake_targets/build_oai

## Step 4 – Run the gNB with rfsim Mode

First, make sure the config file exists:
ls targets/PROJECTS/GENERIC-NR-5GC/CONF/

If not found, download manually from:
https://gitlab.eurecom.fr/oai/openairinterface5g/-/blob/develop/targets/PROJECTS/GENERIC-NR-5GC/CONF/gnb.sa.band78.fr1.106PRB.usrpb210.conf

Then, run the gNB:

sudo ./cmake_targets/ran_build/build/nr-softmodem \
  -O targets/PROJECTS/GENERIC-NR-5GC/CONF/gnb.sa.band78.fr1.106PRB.usrpb210.conf \
  --gNBs.[0].min_rxtxtime 6 --rfsim --sa

## Expected Output

[NR_MAC]   Frame.Slot 0.0  
[NR_MAC]   Frame.Slot 128.0  
[NR_MAC]   Frame.Slot 256.0  
...
