# Solanum-Lycopersicum-Phylogenomic-Analysis
A beginner bioinformatics project, Phylogenomic Analysis of Solanum Lycopersicum (ongoing)

I am starting these mini projects to get hands-on experience, understanding and familiarity of bioinformatics.
Feel free to reach out to me at ajwadsharaheel@gmail.com to give any suggestions or advice.

Below are the steps for me to remember, and for anyone to follow along 

Step # 1
Installed NCBI's Entrez Direct (edirect) command line tool (on linux) to download data directly from the terminal

sh -c "$(curl -fsSL https://ftp.ncbi.nlm.nih.gov/entrez/entrezdirect/install-edirect.sh)"

after installation, user is automatically prompted to add the software to PATH. Enter Y (yes).

Step # 2
Downloaded Chloroplast Genome data for different Solanum Species from NCBI using the following command:
(downloads complete genome data)

esearch -db nucleotide -query "(Solanum tuberosum[Organism] OR Solanum melongena[Organism] OR Solanum nigrum[Organism] OR Solanum lycopersicum[Organism] OR Solanum phureja[Organism]) AND chloroplast[Title] AND \"complete genome\"[Title]" | \
efetch -format fasta > solanum_complete_chloroplasts.fasta

This operation will end with a finished solanum_complete_chloroplasts.fasta file.

Step # 3
Used the following python script to search and isolate the names of the downloaded genomes (and their species)

input_file = 'your_input_file.fasta'  # Replace with your actual input file name
output_file = 'filtered_complete_genomes.fasta'

with open(input_file, 'r') as infile, open(output_file, 'w') as outfile:
    # Initialize a flag to indicate if the current line is a match
    match_found = False
    
    # Iterate through each line in the input file
    for line in infile:
        # Check if the line contains both "Solanum" and "chloroplast, complete genome"
        if 'solanum' in line.lower() and 'chloroplast, complete genome' in line.lower():
            # Write the matching line to the output file
            outfile.write(line)
            match_found = True  # Set the flag to indicate a match was found
        elif match_found:
            match_found = False  # Reset the flag for the next match

print(f"Filtered complete genomes have been written to {output_file}.")


Step # 4
Uploaded the fasta file from Step # 2 (solanum_complete_chloroplasts.fasta) to MAFFT Online Server for alignment

Step # 4a
If the above step fails, then I will reduce the number of complete genome sequences being fed to MAFFT.

Next Steps:
Use the aligned genome sequence file to Build a Phylogenetic Tree using the following command in Terminal:

iqtree -s aligned.fasta -m MFP -bb 1000 -nt AUTO

Visualize the Tree using FigTree Software or online tools like iTOL:

Summarize the Results:
(e.g., tree interpretation, GC% trends).
Create plots with Python (Matplotlib, Seaborn) etc.
