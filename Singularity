Bootstrap: docker
From: willmclaren/ensembl-vep

%help
This is a singularity file for VEP docker (v1)	

%post
	mkdir -p $HOME/.vep;
	mkdir -p $HOME/vep_genomes;
	perl $HOME/INSTALL.pl -a acf -s Saccharomyces_cerevisiae -y R64-1-1 -c $HOME/.vep
	perl $HOME/INSTALL.pl -a acf -s homo_sapiens -y GRCh37 -c $HOME/.vep
	
	git clone https://github.com/Ensembl/VEP_plugins.git
	git clone https://github.com/griffithlab/pVAC-Seq.git
	cp $HOME/pVAC-Seq/pvacseq/VEP_plugins/Wildtype.pm $HOME/VEP_plugins
	rm -r $HOME/pVAC-Seq
	
	
%runscript
	./vep "$@"

