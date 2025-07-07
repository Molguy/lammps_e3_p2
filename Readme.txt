Ejemplo 3 - Cálculo de densidad, RDF y coeficiente de autodifusión de dos diferentes modelos de agua SPC y TIP4P_2005

En la carpeta deben estar los siguientes archivos:
 a) input_water.dat
 b) forcefield.SPC.dat 
 c) forcefield_TIP4P_05.dat
 d) singleSPC.dat
 e) singleTIP4P_05.dat

Temperatura = 298.15 K, Presión = 1 atm

(A) SPC
1. Ejecutar el programa usando:
 1) ./lmp_serial < input_water.dat
 2) o lammps < input.dat (Homebrew)

2. Observar el comprtamiento de la densidad en el archivo wat.dens
 cat wat.dens 

3. Obtener RDF depurando la salida y guardarla en un archivo denominado RDFw.rdf usando: 
 tail -1000 wat.rdf > RDFw.rdf

4. Seleccionar las columnas 2 y 3 y guardar el archivo en RDFCOMwat.rdf usando:
 awk '{print $2, $3}' RDFw.rdf > RDFwat.rdf

5. Elaborar la gráfica en xmgrace usando:
 xmgrace RDFwat.rdf

6. Obtener el coeficiente de atodifusión depurando la salida y guardar en un archivo diff usando:
 tail -200 wat.diff > water.diff

7. Elaborar la gráfica en xmgrace usando:
 xmgrace water.diff


(B) TIP4P_2005
 
8. Modificar el archivo de entrada input_water.dat, cambiando las entradas de
 a) read_data singleSPC.dat a singleTIP4P_05.dat
 a) include forcefield.SCP.dat a forcefield.TIP4P_05.dat
 c) el nombre de los demás archivos que están escritos
	guarda, comparar densidades y RDF

9. Repetir los pasos 1*, 3 al 5 para generar las graficas RDF:   
 a) mpirun -np 4 lmp_mpi -in input_watter.dat   
 b) tail -1000 twat.rdf > RDFtw.rdf
 c) awk '{print $2, $3}' RDFtw.rdf > RDFtwat.rdf
 d) xmgrace RDFtwat.rdf

8. Comparar RDF de SPC y TIP4P_05 usando:
  xmgrace RDFwat.rdf RDFtwat.rdf

10.Obtener el coeficiente de atodifusión del twat para generar su grafica:
 a) tail -200 twat.diff > watter.diff
 c) xmgrace watter.diff
 
11.Comparar coeficiente de autodifusón de SPC y TIP4P_05 usando:
  xmgrace watter.diff water.diff

 
