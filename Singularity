Bootstrap: docker
From: willmclaren/ensembl-vep

%help
This is a singularity file for VEP docker (v1)	

%post
	mkdir -p ${SINGULARITY_ROOTFS}/.vep;
	mkdir -p ${SINGULARITY_ROOTFS}/vep_genomes;
	perl ${SINGULARITY_ROOTFS}/INSTALL.pl -a acf -s Saccharomyces_cerevisiae -y R64-1-1 -c ${SINGULARITY_ROOTFS}/.vep
	perl ${SINGULARITY_ROOTFS}/INSTALL.pl -a acf -s homo_sapiens -y GRCh37 -c ${SINGULARITY_ROOTFS}/.vep
	
	git clone https://github.com/Ensembl/VEP_plugins.git
	git clone https://github.com/griffithlab/pVAC-Seq.git
	cp ${SINGULARITY_ROOTFS}/pVAC-Seq/pvacseq/VEP_plugins/Wildtype.pm ${SINGULARITY_ROOTFS}/VEP_plugins
	rm -r ${SINGULARITY_ROOTFS}/pVAC-Seq
	
	
%runscript
	./vep "$@"

