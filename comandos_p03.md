# Comandos de la Práctica 01
**Nombre(s) Apellido(s)**
En esta practica voy a escribir los comandos que utilice para poder realizar la tarea con la siguiente notacion [comando] [opciones] [argumentos]


## Parte I. 

**Respuesta 1:** Creación de directorios y archivos.
Comandos: 
[mkdir] [] [GenomicaComputacional]
[touch] [] [yjaramillo_p03]
[touch] [] [comandos_p03.md]


**Respuesta 2:** Tipo de shell.

Comando:
[echo] [$0] []

Output:
/usr/bin/zsh

### Tuve que cambiar de zsh a bash.

Comando:
[exec] [] [bash]
[echo] [$0] []

Output:
bash

**Respuesta 3:** Creación de directorios para proyecto bioinformático.

Comandos:
[mkdir] [] [data filtered raw_data meta scripts figures archive]
[tree] [GemomicaComputacional]

Output:

GenomicaComputacional/
├── comandos_p03.md
├── data
│   ├── filtered
│   └── raw_data
├── figures
├── archive
├── meta
├── scripts
└── yjaramillo_p03

7 directories, 2 files

[mv] [filtered data]
[mv] [raw_data data]
[tree] [data]

output: 

data
├── filtered
└── raw_data

2 directories, 0 files



**Respuesta 4:**

Para un proyecto bioinformatico se requieren datos crudos, datos procesados, scripts y documentacion para poder correr analisis.

A continuacion explicare cada una de los directorios:

Data: Aqui se almacenan los datos geneticos, tendremos tanto datos crudos como datos procesados en diferentes directorios.


Meta: Aqui se guardan los metadatos, se puede almacenar informacion de los datos en la carpeta data o bien meter esta carpeta meta en data, si se requieren especificacines para procesar los datos esas especificaciones se pueden guardar aqui.

Scripts: Aqui se guarda el codigo que corre los analisis sobre los datos.

Figures: Aqui puedes hacer las figuras de una publicacion dada.

Archive: Este directorio no se sube al repo es para correr scripts que igual y no usaras al final.


## Parte II.

**Respuesta 1:**

[touch] [] [scripts/delay.sh]
[tree] [] [scripts]

Output: 

scripts
└── delay.sh

0 directories, 1 file

**Respuesta 2:**

[sudo chmod] [a+rwx] [delay.sh]

**Respuesta 3:**

Antes: 
[ll] [] []
Output: 
-rw-rw-r-- 1 berith berith   91 dic  6 15:21 delay.sh

Despues: 
[ll] [] []
Output: 
-rwxrwxrwx 1 berith berith   91 dic  6 15:21 delay.sh*


**Respuesta 4:**
Agregue al codigo delay.sh el siguiente codigo:


#!/bin/bash
echo "Después de la Parte I. necesito un descanso de exactamente 30 segundos."

sleep 30s

echo "Ya puedo continuar!"

Lo probe corriendo y funciono a la perfeccion.

[./delay.sh]

**Respuesta 5:**
Corri el siguiente comando para controlar el PID donde corra mi programa delay.sh

./delay.sh & [1] 38846

Posterior mente lo mate con 
[kill] [-9] [38846]

y cheque que no existiera con:
[top]

## Parte III.

**Respuesta 1:**

El resumen se encuentra en el texto SrsCov-2.txt en el directorio meta.


**Respuesta 2:**
Desde el repositorio de github descargue los archivos y los movi usando la interfaz de ubuntu para ponerlos en el directorio raw_data.

## Parte IV.

**Respuesta 1:**
corri los siguientes comandos desde el folder filtered

ln -s ../raw_data/splike_a.faa

ln -s ../raw_data/splike_b.faa

ln -s ../raw_data/splike_c.faa

Para comprobar el correcto funcionamiento corri el siguiente comando: 

tree filtered

Output: 

filtered
├── glycoproteins.faa
├── splike_a.faa -> ../raw_data/splike_a.faa
├── splike_b.faa -> ../raw_data/splike_b.faa
└── splike_c.faa -> ../raw_data/splike_c.faa

0 directories, 4 files

**Respuesta 2:**
desde el directorio de data corri los siguientes comandos:
[touch] [] [glycoproteins.faa]


**Respuesta 3:**
Desde el directorio filtered donde cree mis ligas suaves (para comprobar que funcionan) corri el siguiente comando:

awk 'NR == 1' splike_a.faa && awk 'NR == 1' splike_b.faa && awk 'NR == 1' splike_c.faa

Output: 
' splike_b.faa && awk 'NR == 1' splike_c.faa 
>gi|1820436168|pdb|6VXX|A Chain A, Spike glycoprotein

>gi|1820436169|pdb|6VXX|B Chain B, Spike glycoprotein

>gi|1820436170|pdb|6VXX|C Chain C, Spike glycoprotein

**Respuesta 4:**
Corri el siguiente comando desde el directorio filtered para redireccionar el contenido de los archivos de interes.

cat splike_*.faa | tee splike_a.faa >glycoproteins.faa

tras hacer eso corri un cat en el file glycoproteins.faa para checar el orden y todo estuvo correcto.


**Respuesta 5:**

Desde el directorio GenomicaComputacional corri el siguiente comando: 

mv data/raw_data/splike_*.faa archive

para comprobar que se hayan movido correctamente los files corri 

tree archive

Output: 
archive
├── splike_a.faa
├── splike_b.faa
└── splike_c.faa

0 directories, 3 files

Que paso con las ligas suaves? 

Ya que los files tenian un cierto path '../../etc' y su lugar fue cambiado a otro path, las ligas suaves perdieron conexion y cambiaron de color verde a rojo denotando que es un path a un file no existente.


**Respuesta 6:**
Corri el siguiente comando que imprime las primeras 3 lineas de un archivo compreso.

zcat SRR10971381_R1.fastq.gz | head -n 3 & 
zcat sarscov2_assembly.fasta.gz | head -n 3 & 
zcat SRR10971381_R2.fastq.gz | head -n 3


**Respuesta 7:**

Solo una de los tres files tiene el caracter > en la primera linea.

**Respuesta 8:**
Corri el siguiente comando:

zcat SRR10971381_R2.fastq.gz | head -n 12

Output: 
@SRR10971381.512_2
CGTGGAGTATGGCTACATACTACTTATTTGATGAGTCTGGTGAGTTTAAAGTGGCTTCACATATGTATTGTTCTTTCTACCCTCCAGATGAGGATGAAGAAGAAGGTGATTGTGAAGAAGAAGAGTTTGAGCCATCAACTCAATATGAGT
+
/FFFA/A/FFFF66FFFFFF/FF/FFFFFFFFFFFFF/AFFF6FFFA6FFFFF/FFFFFFFFFFFFFFFFFF/FF/FFFFFA/FFF/FFF/A/AFA/FFFFF/=F/F/F/AFAFF//A/AFF//FFAF/FFF=FFAFFFA/A/6=///==
@SRR10971381.556_2
TTTGTAAAAATAAAATAAAAAAAATAAAAATAATATATTAAAAAAAGATAAATAAAAAAATGAACAATTAATAAAAAAAAAAAAAAAAAAAAATTAAAAAAAAAAAAAAAAAAAATAAAAAAAAAAAAAAATAAAAAAAAAATTATAAAA
+
6AFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF/FFFAFFFFFF/FFA/FF=F//=FF/FFFFFFFFFFFFFA/FFFF/FF/FA//F/FFFFFFA/=FFFFF/FFFF/F=FFFAFF///FFFFA/FF/6//////=/
@SRR10971381.1428_2
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
+
FFFFFFFFFFFFAFFFAFFFFFF6A//F//FFF

**Respuesta 9:**
Fasta: Es un formato de texto plano que contiene las secuencias crudas, este formato es el que otorgan las plataformas de secuenciación.

Fastaq: Es una variante del formato FASTA, solo que tiene asociado datos sobre la calidad de cada secuencia.

fasta vs faa: Fasta puede ser proteina o nucleotido y faa es usado por la NCBI para FASTA Amino Acids,osea que es una propeina FASTA file.

FastQC: busca proveer una manera simple de hacer control de calidad en una secuencia 'raw' de datos provenientes de pipelines de otras secuencias.

Las secuencias hacer referencias a nucleotidos.


**Respuesta 10**
Tuve que volver a meterme al NCBI para descargar los archivos gff3 que no se encotraban en el github.

Tras correr los comandos less -S sarscov2_genome.gff3 y less sequence.gff3 note que:
La bandera S hace que las lineas no se adapten a la pantalla de la terminal sino que se queden con sui longitud, si no se pone la bandera todo se va a adaptar a la terminal por default.

**Respuesta 11**
Corri el comando
awk '{if($3 =="gene") print; ++n;}' sequence.gff3

Output:

NC_045512.2	RefSeq	gene	266	21555	.	+	.	ID=gene-GU280_gp01;Dbxref=GeneID:43740578;Name=ORF1ab;gbkey=Gene;gene=ORF1ab;gene_biotype=protein_coding;locus_tag=GU280_gp01
NC_045512.2	RefSeq	gene	21563	25384	.	+	.	ID=gene-GU280_gp02;Dbxref=GeneID:43740568;Name=S;gbkey=Gene;gene=S;gene_biotype=protein_coding;gene_synonym=spike glycoprotein;locus_tag=GU280_gp02
NC_045512.2	RefSeq	gene	25393	26220	.	+	.	ID=gene-GU280_gp03;Dbxref=GeneID:43740569;Name=ORF3a;gbkey=Gene;gene=ORF3a;gene_biotype=protein_coding;locus_tag=GU280_gp03
NC_045512.2	RefSeq	gene	26245	26472	.	+	.	ID=gene-GU280_gp04;Dbxref=GeneID:43740570;Name=E;gbkey=Gene;gene=E;gene_biotype=protein_coding;locus_tag=GU280_gp04
NC_045512.2	RefSeq	gene	26523	27191	.	+	.	ID=gene-GU280_gp05;Dbxref=GeneID:43740571;Name=M;gbkey=Gene;gene=M;gene_biotype=protein_coding;locus_tag=GU280_gp05
NC_045512.2	RefSeq	gene	27202	27387	.	+	.	ID=gene-GU280_gp06;Dbxref=GeneID:43740572;Name=ORF6;gbkey=Gene;gene=ORF6;gene_biotype=protein_coding;locus_tag=GU280_gp06
NC_045512.2	RefSeq	gene	27394	27759	.	+	.	ID=gene-GU280_gp07;Dbxref=GeneID:43740573;Name=ORF7a;gbkey=Gene;gene=ORF7a;gene_biotype=protein_coding;locus_tag=GU280_gp07
NC_045512.2	RefSeq	gene	27756	27887	.	+	.	ID=gene-GU280_gp08;Dbxref=GeneID:43740574;Name=ORF7b;gbkey=Gene;gene=ORF7b;gene_biotype=protein_coding;locus_tag=GU280_gp08
NC_045512.2	RefSeq	gene	27894	28259	.	+	.	ID=gene-GU280_gp09;Dbxref=GeneID:43740577;Name=ORF8;gbkey=Gene;gene=ORF8;gene_biotype=protein_coding;locus_tag=GU280_gp09
NC_045512.2	RefSeq	gene	28274	29533	.	+	.	ID=gene-GU280_gp10;Dbxref=GeneID:43740575;Name=N;gbkey=Gene;gene=N;gene_biotype=protein_coding;locus_tag=GU280_gp10
NC_045512.2	RefSeq	gene	29558	29674	.	+	.	ID=gene-GU280_gp11;Dbxref=GeneID:43740576;Name=ORF10;gbkey=Gene;gene=ORF10;gene_biotype=protein_coding;locus_tag=GU280_gp11


Para saber la cantidad de genes en el file use:

awk ' BEGIN {  print "The number of times gene appears in the file is: " ; } {if($3 == "gene"){counter+=1;}} END {  printf "%s\n",  counter  ; } '  sequence.gff3

Output: 

The number of times gene appears in the file is: 
11

El campo 3 es ya sea un termino del Sequence ONtology o un numero SO de accession'.

Gen vs CDS: un CDS se refiere a los exones y dos codones los cuales son el de inicio y el que se usa para parar, su secuencia se traduce a una proteina, el gen tiene cds y no cds.


## Parte V.

**Respuesta 1**
En el directorio figures corri.

ln -s ../data/raw_data/sarscov2_genome.gff3

**Respuesta 2**


awk -F '\t' ' BEGIN{g = "The number of times a gene appears in the file is: "}
{cds = "The number of times a cds appears in the file is: "}
{stem_loop = "The number of times a stem_loop appears in the file is: "}
{mature_protein_region_of_CDS = "The number of times a mature_protein_region_of_CDS appears in the file is: "}
{three_prime_UTR = "The number of times a three_prime_UTR appears in the file is: "}
{five_prime_UTR = "The number of times a five_prime_UTR appears in the file is: "}
{if($3 == "mature_protein_region_of_CDS"){proteinCounter+=1;}}
{if($3 == "three_prime_UTR"){threeCounter+=1;}}
{if($3 == "five_prime_UTR"){fiveCounter+=1;}}
{if($3 == "CDS"){cdsCounter+=1;}}
{if($3 == "stem_loop"){loopCounter+=1;}}{if($3 == "CDS"){cdsCounter+=1;}} 
{if($3 == "gene"){geneCounter+=1;}} END {  print g geneCounter; print cds cdsCounter; print mature_protein_region_of_CDS proteinCounter; print stem_loop loopCounter; print three_prime_UTR threeCounter; print five_prime_UTR fiveCounter;} '  sarscov2_genome.gff3 > barplot_data.txt


**Respuesta 3**

No entendi la pregunta







