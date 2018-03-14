Bootstrap: docker
From: willmclaren/ensembl-vep

%help
This is a singularity file for VEP docker (v1)	

%post
	mkdir -p ${SINGULARITY_ROOTFS}/.vep;
	mkdir -p ${SINGULARITY_ROOTFS}/vep_genomes;
	git clone https://github.com/Ensembl/VEP_plugins.git
	git clone https://github.com/griffithlab/pVAC-Seq.git
	cp ${SINGULARITY_ROOTFS}/pVAC-Seq/pvacseq/VEP_plugins/Wildtype.pm ${SINGULARITY_ROOTFS}/VEP_plugins
	rm -r ${SINGULARITY_ROOTFS}/pVAC-Seq
	
	
%runscript
	/home/vep/src/ensembl-vep/vep "$@"

