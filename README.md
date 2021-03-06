secuenciacion de 102 variedades baja cobertura
secuenciacion de 30 variedades alta cobertura

CNV Genomes A B D
Variantes

identificar genes en el pangenoma
hacer una tabla con gen, existe o no en la variedad, tiene variante




INFO SOBRE SEQUENCIACION

Hola Juan!
Los/el amplicon(es) se secuenciaron con tecnología Illumina, en concreto con un equipo MiSeq, en formato pair end (PE) con lecturas de 150 pb de largo. Eso quiere decir que hay una lectura "forward" y una lectura "reverse", que según el tamaño del amplicón se van a solapar en el centro o no (o sea, si los amplicones son de 200 bases, 150 bases están en las lecturas "forward", 150 bases están en las lecturas "reverse" y hay un solapamiento de 100 bases leidas por las dos orientaciones de las lecturas; si los amplicones son de 300 bases no hay solapamiento, porque cada lectura desde cada extremo llega hasta 150 bases). Estas lecturas son las que les interesan a ustedes porque dan información directa de la secuencia y corresponden a los archivos R1 y R2 del adjunto que les mandó Andrea. Entretanto, las lecturas I2 corresponden a los índices utilizados y sólo sirven para el reconocimiento de la muestra. En la mayoría de los casos no es necesario este archivo, ya que la información de interés está en los otros dos.
Yo realizo el análisis bioinformático con linux, y constan de tres pasos básicos: chequeo de calidad, mapeo a una referencia e identificación de variantes respecto de la referencia. Para el primer paso utilizo el programa FastQC para un chequeo inicial de calidad de las secuencias. No miré las secuencias de ustedes así que no tengo información al respecto. Conviene hacer en este paso si fuera necesario un recorte de bases de baja calidad o de adaptadores. Para eso uso el programa Trimmomatic, pero hay otros programas disponibles también. Los adaptadores utilizados en el caso de ustedes son: 
 
R94: CAAGCAGAAGACGGCATACGAGATTATCGGGAGTGACTGGAGTTCAGACGTG
F6: AATGATACGGCGACCACCGAGATCTACACACTGCATAACACTCTTTCCCTACACGA

Al aplicar el programa Trimmomatic se pueden eliminar adaptadores que eventualmente hayan sido secuenciados junto con las lecturas de la región de interés, aunque no siempre es el caso. Yo lo metería por las dudas, sobre todo si no tienen mucha experiencia en visualización de calidad con FastQC.
 
En la etapa de mapeo uso programas como BWA-mem o Bowtie2. El archivo de referencia en el caso de ustedes debería ser el genoma de trigo, ya que buscan una familia multigénica. De esa forma se garantizan mapear todo lo que haya sido amplificado en las distintas regiones del genoma posibles.
Después del mapeo pueden visualizar los resultados con programas como Tablet, lo que les va a dar una aproximación más amigable de las diferentes cosas que mapearon.
Finalmente queda la identificación de variantes, de interesarles, lo que igual en principio entiendo que no es lo que más les interesa, pero que sería interesante evaluar a la larga. Para eso también existen diferentes programas como GATK, VarScan y otros.
Imagino que tendrán algun contacto que les pueda dar alguna asistencia para el análisis bioinformático si es que todavía no están familiarizados. Este mail sirve como primera aproximación y un ejemplo en este caso de cómo suelo manejar yo este tipo de datos, pero por supuesto existen otras posibilidades.
Cualquier cosa estamos en contacto.
Saludos,
Mónica
