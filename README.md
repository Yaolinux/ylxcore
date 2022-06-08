# YLXCORE
The collection of scripts for build a Yaolinux :)

## Prepare host system

 1. Create two partitions 
	 - DATA - EXT4
	 - SWAP
 2. Format the partition
 3. Clone this repository
 4. Complete or replace the partitions "scripts/config"
 5. Launch the script "init"

## Enter in build

 1. Verify the command "echo $LFS". The out must be "/mnt/lfs"
 2. Change user in "lfs". "su - lfs"
 3. Enter the bashrc below this

        cat > ~/.bash_profile << "EOF"
        exec env -i HOME=$HOME TERM=$TERM PS1='\u:\w\$ ' /bin/bash
        EOF
        
        cat > ~/.bashrc << "EOF"
	    set +h
	    umask 022
	    LFS=/mnt/lfs
	    LC_ALL=POSIX
	    LFS_TGT=$(uname -m)-lfs-linux-gnu
		PATH=/usr/bin
	    if [ ! -L /bin ]; then PATH=/bin:$PATH; fi
	    PATH=$LFS/tools/bin:$PATH
	    CONFIG_SITE=$LFS/usr/share/config.site
	    export LFS LC_ALL LFS_TGT PATH CONFIG_SITE
	    EOF
    
	    source ~/.bash_profile


