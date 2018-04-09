Bootstrap: docker
From: ubuntu:16.04


%environment
        R_LIBS_USER=/usr/local/lib/R/site-library/
        export R_LIBS_USER

%post
        apt-get update && apt-get -y upgrade
        gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
        gpg -a --export E084DAB9 | apt-key add -
        echo "deb http://cran.rstudio.com/bin/linux/ubuntu xenial/" | tee -a /etc/apt/sources.list
        apt-get update
	apt-get -y install libssl-dev 
        apt-get -y install libmariadb-client-lgpl-dev 
	apt-get -y install r-base
        apt-get -y install pandoc
        apt-get -y install locales
        locale-gen en_US.UTF-8
	apt-get -y install libcurl4-openssl-dev libxml2-dev
	mkdir -p /lustre

	R --slave -e 'install.packages(c("XML","RCurl","dplyr","reshape2","knitr","rmarkdown","ggplot2","RMySQL"),repos="https://cloud.r-project.org/");source("https://bioconductor.org/biocLite.R");biocLite(c("DESeq2","AnnotationDbi","GenomeInfoDb","TxDb.Athaliana.BioMart.plantsmart28","tximport"))'





