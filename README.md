# RsolaniDB 
Creating local (offline) copy of the database. The offline version can be used to publicly access all the backend scripts, libraries and database files used in the online version of the RsolaniDB. The online version of the database is available at http://rsolanidb.kaust.edu.sa/RhDB/

## About the database
*Rhizoctonia solani Kühn* (teleomorph: Thanatephorus cucumeris [Frank] Donk) is a collective name for a group of ubiquitous, soilborne and multinucleate basidiomycetous fungi, which are classified into 13 Anastomosis Groups (AGs) with interspecific subgroups having distinctive morphology, pathogenicity and heterogenous genetic composition. Here, we performed comprehensive genome sequencing, assembly, annotation and pangenome functional analysis of 12 *R. solani* isolates covering 7 AGs and selected sub-groups (AG1-IA, AG1-IB, AG1-IC, AG2-2IIIB, AG3-PT, AG3-TB, AG4-HG-I, AG5, AG6, and AG8). The results and datasets are compiled as a user-friendly database to host a large repertoire of reference-quality R. solani genomes and their annotated gene models. The genomes of six previously reported R. solani isolates by other research groups are also included in this database. The database stands as a valuable platform for hosting, visualizing, and analyzing highly diverse genome assemblies and their annotated components, with tools for gene enrichment & pathway analysis, sequence retrieval and visualization. Since most of the genomes are reported for the first time, the genomes, gene models and the database can be a useful resource for formulating novel hypotheses across the highly complex pathosystems of *R. solani*  AGs and sub-groups with distinct host preferences. 

## Prerequisite
In order to create a local copy of the database, following softwares and tools are required. Very basic understanding of MySQL and apache-websever architecture is also expected (not mandatory).

```
Operating System: Any UNIX-based OS (e.g. Ubuntu or Mac OS)
Softwares : Apache-server (2.4.29 for Ubuntu or higher) , Perl (5.26.1 or higher), R (version 3.6 or higher) and MySQL (8.0.22 for Linux or higher)
R Libraries: topGO (version 3.12 or higher), bc3net (version 1.0.4 or higher), dplyr (version 1.0 or higher)
Perl Library: CGI
```

## Installation

Step1: Clone the repository
```
git clone https://github.com/abbioinfo/RsolaniDB.git
cd rsolanidb
```
Step2: Update the local copy of MySQL database
```
wget http://rsolanidb.kaust.edu.sa/rsolanidb.sql
mysql -u root -p RsolaniDB < rsolanidb.sql
```
Step3: Update html files in apache-webserver
```
wget http://rsolanidb.kaust.edu.sa/RhDB.zip
unzip RhDB.zip
mv RhDB /var/www/html/
```
Step4: Update cgi-bin files in apache-webserver. This directory contains all the perl and R scripts used in the RsolaniDB database.
```
wget http://rsolanidb.kaust.edu.sa/RhDBcgi.zip
unzip RhDBcgi.zip
mv RhDB /var/www/cgi-bin/
```
!!! Done !!!


**Note**: *The path of cgi-bin directory may be /usr/lib/cgi-bin (or any other directory, instead of /var/www/cgi-bin/). Please check with your apache config file to know the default cgi-bin directory.*

**Note**: *The default password used in the MySQL database scripts is abhi1234. If you are using any other MySQL password, please change the default password in perl scripts or (.pm) modules available in cgi-bin directory.*


## Testing the database 

Open you favourite web-browser (e.g. google chrome) and access the local copy of database using following URL:

http://localhost/RhDB/



# Cite
If you use RsolaniDB for your research. Please [cite](https://www.biorxiv.org/content/10.1101/2020.12.18.423518v1)

```
Pangenome analysis of the soil-borne fungal phytopathogen Rhizoctonia solani and development of a comprehensive web resource: RsolaniDB
A. Kaushik, D.P. Roberts, A. Ramaprasad, S. Mfarrej, Mridul Nair, D.K. Lakshman, A. Pain

bioRxiv 2020.12.18.423518; doi: https://doi.org/10.1101/2020.12.18.423518
```

