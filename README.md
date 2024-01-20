# Parallel-Processing-Using-MPI-CUDA

Certainly! Here's a simple template for a README file for your Parallel Processing Lab:

## Installation of MPI in Visual Studio Code

- **To install MPI, see this [video](https://www.youtube.com/watch?v=bkfCrj-rBjU) & follow every step carefully. If you face the issue "sal.h dependency not found" or something like that, uninstall the MinGW compiler & follow this [video](https://www.youtube.com/watch?v=_-O94qsnOLk)**

### Run Command on Visual Studio Code

- **To run a C Program, go to `Terminal` > `Run Build Task...` in the VS Code & then run the following command**
<pre>
<b>mpiexec -n number_of_processors file_name_without_extension</b>
</pre>

## Installation of MPI in Windows Subsystem for Linux

- **Go to `Turn Windows features on or off` & turn on the `Windows Subsystem for Linux`**
- **Now go to windows Terminal & run the 1st command (if doesn't work run the 2nd command)**
<pre>
<b>wsl.exe --install</b>
<b>wsl --install -d Ubuntu-22.04</b>
</pre>
- **If any error occurs go to the provided link & download the latest package from `Step 4 - Download the Linux kernel update package`**
- **If further error occurs with error code `0x80370102` go to Terminal & run the following command**
<pre>
<b>wsl --update</b>
<b>wsl --set-default-version 1</b>
</pre>
- **Now go to `Ubunto` & Setup with Username & Password**
- **Then run the following commands on `Ubunto`**
<pre>
<b>sudo apt-get update</b>
<b>sudo apt-get install mpich</b>
</pre>
- **Once after every session you have to mount your drive using the command**
<pre>
<b>cd /mnt/(C/D/E/F)</b>
</pre>

### Run Command on Ubuntu

- **To run a C Program, go to `Ubuntu` & then run the following commands**
<pre>
<b>mpicc name.c -o name</b>
<b>mpirun -n number_of_processors ./name</b>  
</pre>
- **To run a C++ Program, go to `Ubuntu` & then run the following commands**
<pre>
<b>mpic++ name.c -o name</b>
<b>mpirun -n number_of_processors ./name</b>  
</pre>

## Lab Tasks



- Write a program to multiply K different matrices A of dimension MxN with matrices B
of dimension NxP dimension matrices. Where K is the number of matrices.
K * M * N <= 10^6; K * N * P<= 10^6; K * M * P <= 10^6;
(a). Using MPI
(b). Using CUDA
Input: K, M, N, P
Output: Time taken for multiplication

- Write a program to count the words in a file and sort it in descending order of frequency
of words i.e., highest occurring word must come first and the least occurring word must
come last.
(a). Using MPI
(b). Using CUDA
Input: No. of processes, (Text input from file)
Output: Total time, top 10 occurrences

- A phonebook is given as a file. Write a program to search for all the contacts matching a
name.
(a). Using MPI
(b). Using CUDA
Input: No. of processes, (phonebook from file)
Output: Total time, Matching names and contact numbers

- Given a paragraph and a pattern like %x%, write a program to find out the number of
occurrences of the given pattern inside the text.
(a). Using MPI
(b). Using CUDA
Input: No. of processes, (paragraph from file)
Output: Total time, No. of occurrences of the patter

## Basic Instructions of MPI

- **To configure the program to run an MPI, initialize all the data structures -**
<pre>
<b>int MPI_Init(int *argc, char ***argv)</b>
</pre>
- **To stop the process & turn of any communication -**
<pre>
<b>int MPI_Finalize()</b>
</pre>
- **To get the number of processes -**
<pre>
<b>int MPI_Comm_size(MPI_Comm comm, int *size)</b>
</pre>
- **To get the local processes index -**
<pre>
<b>int MPI_Comm_rank(MPI_Comm comm, int *rank)</b>
</pre>
- **To send information -**
<pre>
<b>int MPI_Send(void *buf, int count, MPI_Datatype datatype, int dest, int tag, MPI_Comm comm)</b>
</pre>
- **To receive information -**
<pre>
<b>int MPI_Recv(void *buf, int count, MPI_Datatype datatype, int source, int tag, MPI_Comm comm, MPI_Status *status)</b>
</pre>

# Parallel Processing Lab

## Table of Contents

1. [Matrix Multiplication](#matrix-multiplication)
2. [Word Count and Sorting](#word-count-and-sorting)
3. [Phonebook Search](#phonebook-search)
4. [Pattern Occurrence Count](#pattern-occurrence-count)

## Matrix Multiplication

### Using MPI

```bash
mpiexec -n <number_of_processes> ./matrix_multiplication_mpi <K> <M> <N> <P>
```

- `<number_of_processes>`: Number of MPI processes.
- `<K>`, `<M>`, `<N>`, `<P>`: Matrix dimensions.

### Using CUDA

```bash
./matrix_multiplication_cuda <K> <M> <N> <P>
```

- `<K>`, `<M>`, `<N>`, `<P>`: Matrix dimensions.

Output: Time taken for multiplication.

## Word Count and Sorting

### Using MPI

```bash
mpiexec -n <number_of_processes> ./word_count_mpi <filename>
```

- `<number_of_processes>`: Number of MPI processes.
- `<filename>`: Input file containing text.

### Using CUDA

```bash
./word_count_cuda <filename>
```

- `<filename>`: Input file containing text.

Output: Total time, top 10 occurrences.

## Phonebook Search

### Using MPI

```bash
mpiexec -n <number_of_processes> ./phonebook_search_mpi <filename> <search_name>
```

- `<number_of_processes>`: Number of MPI processes.
- `<filename>`: Phonebook file.
- `<search_name>`: Name to search for.

Output: Total time, matching names and contact numbers.

## Pattern Occurrence Count

### Using MPI

```bash
mpiexec -n <number_of_processes> ./pattern_occurrence_mpi <filename> <pattern>
```

- `<number_of_processes>`: Number of MPI processes.
- `<filename>`: Input file containing text.
- `<pattern>`: Pattern to search for.

### Using CUDA

```bash
./pattern_occurrence_cuda <filename> <pattern>
```

- `<filename>`: Input file containing text.
- `<pattern>`: Pattern to search for.
