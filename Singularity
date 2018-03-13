Bootstrap: docker
From: willmclaren/ensembl-vep

%help
This is a singularity file for VEP docker (v1)

%post
	mkdir -p ./.vep;
	mkdir -p ./vep_genomes;
	./INSTALL.pl -a acf -s Saccharomyces_cerevisiae -y R64-1-1 -c ./.vep
	./INSTALL.pl -a acf -s homo_sapiens -y GRCh37 -c ./.vep
	
	git clone https://github.com/Ensembl/VEP_plugins.git
	git clone https://github.com/griffithlab/pVAC-Seq.git
	cp ./pVAC-Seq/pvacseq/VEP_plugins/Wildtype.pm ./VEP_plugins
	rm -r ./pVAC-Seq
	
	
%runscript
	./vep "$@"

