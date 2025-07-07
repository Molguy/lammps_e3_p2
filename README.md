# lammps_e3_p2
Instructivo, archivos de entrada y log's de la simulación del ejemplo 3 parte 2

    export OMP_NUM_THREADS=2
    
Comandos para SPC:
    
    mpirun -np 2 lmp_mpi < input_water.dat
.
    
    tail -1000 wat.rdf | awk '{print $2, $3}' > RDFwat.rdf
.
    
    tail -200 wat.diff > water.diff

Comandos para TIP4P_05:  

    mpirun -np 4 lmp_mpi < input_water.dat
.
    
    tail -1000 twat.rdf | awk '{print $2, $3}' > RDFtwat.rdf
.
    
    tail -200 twat.diff > watter.diff

Comando para las graficas comparativas

    xmgrace RDFtwat.rdf RDFwat.rdf && xmgrace watter.diff water.diff 
