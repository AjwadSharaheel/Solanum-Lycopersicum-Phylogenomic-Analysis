# Solanum-Lycopersicum-Phylogenomic-Analysis
A beginner bioinformatics project, Phylogenomic Analysis of Solanum Lycopersicum (ongoing)

I am starting these mini projects to get hands-on experience, understanding and familiarity of bioinformatics.
Feel free to reach out to me at ajwadsharaheel@gmail.com to give any suggestions or advice.

Below are the steps for me to remember, and for anyone to follow along 



## Step # 1
Installed NCBI's Entrez Direct (edirect) command line tool (on linux) to download data directly from the terminal

sh -c "$(curl -fsSL https://ftp.ncbi.nlm.nih.gov/entrez/entrezdirect/install-edirect.sh)"

after installation, user is automatically prompted to add the software to PATH. Enter Y (yes).



## Step # 2
Downloaded Chloroplast Genome data for different Solanum Species from NCBI using the following command:
(downloads complete genome data)

    esearch -db nucleotide -query "(Solanum tuberosum[Organism] OR Solanum melongena[Organism] OR Solanum nigrum[Organism] OR Solanum lycopersicum[Organism] OR Solanum phureja[Organism]) AND chloroplast[Title] AND \"complete genome\"[Title]" | \
    efetch -format fasta > solanum_complete_chloroplasts.fasta

This operation will end with a finished solanum_complete_chloroplasts.fasta file.



## Step # 3
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



## Step # 4
Uploaded the fasta file from Step # 2 (solanum_complete_chloroplasts.fasta) to MAFFT Online Server for alignment



## Step # 4a
If the above step fails, then I will reduce the number of complete genome sequences being fed to MAFFT. Currently I have the following complete genome sequences sent for aignment. Would any experienced person mind tooking a look below and point out how many (and which ones) sequences do I need to perform simple phylogenomic analysis and make a phylogenetic tree ?


>PP579975.1 Solanum tuberosum isolate C88 chloroplast, complete genome<br>
>PP579974.1 Solanum phureja isolate IVP101 chloroplast, complete genome<br>
>OP688482.1 Solanum melongena cultivar Yunqie 9 chloroplast, complete genome<br>
>PP680311.1 Solanum phureja chloroplast, complete genome<br>
>PP680310.1 Solanum tuberosum chloroplast, complete genome<br>
>PP091928.1 Solanum lycopersicum isolate M82 chloroplast, complete genome<br>
>PP091926.1 Solanum lycopersicum isolate FQM chloroplast, complete genome<br>
>PP432013.1 Solanum tuberosum cultivar White Lady chloroplast, complete genome<br>
>ON509849.1 Solanum tuberosum voucher PI 607886 chloroplast, complete genome<br>
>ON509841.1 Solanum tuberosum voucher PI 558142 chloroplast, complete genome<br>
>ON509839.1 Solanum tuberosum voucher PI 546023 chloroplast, complete genome<br>
>ON509825.1 Solanum tuberosum voucher PI 214421 chloroplast, complete genome<br>
>ON509698.1 Solanum tuberosum voucher CIP 703515 chloroplast, complete genome<br>
>ON509697.1 Solanum tuberosum voucher CIP 703514 chloroplast, complete genome<br>
>ON509696.1 Solanum tuberosum voucher CIP 703511 chloroplast, complete genome<br>
>ON509695.1 Solanum tuberosum voucher CIP 703510 chloroplast, complete genome<br>
>ON509694.1 Solanum tuberosum voucher CIP 703509 chloroplast, complete genome<br>
>ON509693.1 Solanum tuberosum voucher CIP 703508 chloroplast, complete genome<br>
>ON509692.1 Solanum tuberosum voucher CIP 703473 chloroplast, complete genome<br>
>ON509691.1 Solanum tuberosum voucher CIP 703433 chloroplast, complete genome<br>
>ON509690.1 Solanum tuberosum voucher CIP 703421 chloroplast, complete genome<br>
>ON509689.1 Solanum tuberosum voucher CIP 703352 chloroplast, complete genome<br>
>ON509688.1 Solanum tuberosum voucher CIP 703317 chloroplast, complete genome<br>
>ON509687.1 Solanum tuberosum voucher CIP 703315 chloroplast, complete genome<br>
>ON509686.1 Solanum tuberosum voucher CIP 703312 chloroplast, complete genome<br>
>ON509685.1 Solanum tuberosum voucher CIP 703308 chloroplast, complete genome<br>
>ON509684.1 Solanum tuberosum voucher CIP 703294 chloroplast, complete genome<br>
>OR632702.1 Solanum tuberosum chloroplast, complete genome<br>
>OR632701.1 Solanum tuberosum chloroplast, complete genome<br>
>OR632700.1 Solanum tuberosum chloroplast, complete genome<br>
>OR632699.1 Solanum tuberosum chloroplast, complete genome<br>
>OR632698.1 Solanum tuberosum chloroplast, complete genome<br>
>OR632697.1 Solanum tuberosum chloroplast, complete genome<br>
>OQ865339.1 Solanum tuberosum cultivar Zhukovsky chloroplast, complete genome<br>
>OQ865338.1 Solanum tuberosum cultivar Udacha chloroplast, complete genome<br>
>OQ865337.1 Solanum tuberosum cultivar Symphonia chloroplast, complete genome<br>
>OQ865336.1 Solanum tuberosum cultivar Sudarinya chloroplast, complete genome<br>
>OQ865335.1 Solanum tuberosum cultivar Severnoe siyanie chloroplast, complete genome<br>
>OQ865334.1 Solanum tuberosum cultivar Nikulinsky chloroplast, complete genome<br>
>OQ865333.1 Solanum tuberosum cultivar Nevsky chloroplast, complete genome<br>
>OQ865332.1 Solanum tuberosum cultivar Meteor chloroplast, complete genome<br>
>OQ865331.1 Solanum tuberosum cultivar Krepysh chloroplast, complete genome<br>
>OQ865330.1 Solanum tuberosum cultivar Krasavchik chloroplast, complete genome<br>
>OQ865329.1 Solanum tuberosum cultivar Krasa Meshchery chloroplast, complete genome<br>
>OQ865328.1 Solanum tuberosum cultivar Gusar chloroplast, complete genome<br>
>OQ865327.1 Solanum tuberosum cultivar Grand chloroplast, complete genome<br>
>OQ865326.1 Solanum tuberosum cultivar Golubizna chloroplast, complete genome<br>
>OQ865325.1 Solanum tuberosum cultivar Fritella chloroplast, complete genome<br>
>OQ473549.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473548.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473547.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473546.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473542.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473539.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473538.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473537.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473536.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473535.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473534.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473533.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473532.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473531.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473530.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473529.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473528.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473526.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473525.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473524.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473523.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473522.1 Solanum lycopersicum chloroplast, complete genome<br>
>OQ473521.1 Solanum lycopersicum chloroplast, complete genome<br>
>NC_007898.3 Solanum lycopersicum chloroplast, complete genome<br>
>NC_050207.1 Solanum tuberosum subsp. andigenum isolate ADG1 chloroplast, complete genome<br>
>NC_028070.2 Solanum nigrum chloroplast, complete genome<br>
>NC_008096.2 Solanum tuberosum chloroplast, complete genome<br>
>OP056022.1 Solanum tuberosum chloroplast, complete genome<br>
>OP589401.1 Solanum tuberosum chloroplast, complete genome<br>
>OM638080.1 Solanum tuberosum chloroplast, complete genome<br>
>OM638079.1 Solanum tuberosum chloroplast, complete genome<br>
>MW285079.1 Solanum nigrum clone LK chloroplast, complete genome<br>
>ON641346.1 Solanum nigrum isolate BPTPS120 voucher LISE:96441 chloroplast, complete genome<br>
>MZ030724.1 Solanum tuberosum cultivar Spunta chloroplast, complete genome<br>
>MZ030723.1 Solanum tuberosum cultivar Colomba chloroplast, complete genome<br>
>MZ030722.1 Solanum tuberosum cultivar Castle Russet chloroplast, complete genome<br>
>MZ030721.1 Solanum tuberosum cultivar Avenger chloroplast, complete genome<br>
>MZ030720.1 Solanum tuberosum cultivar Atlantic chloroplast, complete genome<br>
>MZ030719.1 Solanum tuberosum cultivar Altus chloroplast, complete genome<br>
>MT621037.1 Solanum nigrum chloroplast, complete genome<br>
>MZ221866.1 Solanum nigrum voucher HFN:A14750130 chloroplast, complete genome<br>
>MZ221865.1 Solanum nigrum voucher NY:Nee 45551 chloroplast, complete genome<br>
>MW384850.1 Solanum melongena chloroplast, complete genome<br>
>MW384849.1 Solanum melongena chloroplast, complete genome<br>
>MW384848.1 Solanum melongena chloroplast, complete genome<br>
>MW384847.1 Solanum melongena chloroplast, complete genome<br>
>MW384846.1 Solanum melongena chloroplast, complete genome<br>
>MW384845.1 Solanum melongena chloroplast, complete genome<br>
>MW384844.1 Solanum melongena chloroplast, complete genome<br>
>MW384840.1 Solanum melongena chloroplast, complete genome<br>
>MW384839.1 Solanum melongena chloroplast, complete genome<br>
>MW384838.1 Solanum melongena chloroplast, complete genome<br>
>MW384837.1 Solanum melongena chloroplast, complete genome<br>
>MW384836.1 Solanum melongena chloroplast, complete genome<br>
>MW384835.1 Solanum melongena chloroplast, complete genome<br>
>MW384834.1 Solanum melongena chloroplast, complete genome<br>
>MW384833.1 Solanum melongena chloroplast, complete genome<br>
>MW384832.1 Solanum melongena chloroplast, complete genome<br>
>MW384831.1 Solanum melongena chloroplast, complete genome<br>
>MW384830.1 Solanum melongena chloroplast, complete genome<br>
>MW384829.1 Solanum melongena chloroplast, complete genome<br>
>MW384828.1 Solanum melongena chloroplast, complete genome<br>
>MW384827.1 Solanum melongena chloroplast, complete genome<br>
>MW384826.1 Solanum melongena chloroplast, complete genome<br>
>MW384825.1 Solanum melongena chloroplast, complete genome<br>
>MW384824.1 Solanum melongena chloroplast, complete genome<br>
>MT511710.1 Solanum tuberosum clone W5281.2 chloroplast, complete genome<br>
>MT511709.1 Solanum tuberosum clone H412-1 chloroplast, complete genome<br>
>MT511708.1 Solanum tuberosum clone DW84-1457 chloroplast, complete genome<br>
>MT511707.1 Solanum tuberosum clone 12625-02 chloroplast, complete genome<br>
>MT511706.1 Solanum tuberosum clone 12120-03 chloroplast, complete genome<br>
>MT511705.1 Solanum tuberosum clone 11379-03 chloroplast, complete genome<br>
>MT511704.1 Solanum tuberosum clone 10908-06 chloroplast, complete genome<br>
>MT511703.1 Solanum tuberosum clone 08675-21 chloroplast, complete genome<br>
>MT511702.1 Solanum tuberosum clone 7506-01 chloroplast, complete genome<br>
>MW307949.1 Solanum tuberosum cultivar Shepody chloroplast, complete genome<br>
>MW307948.1 Solanum tuberosum cultivar Favorita chloroplast, complete genome<br>
>MW307947.1 Solanum tuberosum cultivar Atlantic chloroplast, complete genome<br>
>MW307946.1 Solanum tuberosum cultivar Yanshu No. 4 chloroplast, complete genome<br>
>MT120865.1 Solanum tuberosum isolate TBR chloroplast, complete genome<br>
>MT120862.1 Solanum tuberosum subsp. andigenum isolate ADG2 chloroplast, complete genome<br>
>MT120861.1 Solanum tuberosum subsp. andigenum isolate ADG1 chloroplast, complete genome<br>
>MT120858.1 Solanum phureja isolate PHU chloroplast, complete genome<br>
>MT811796.1 Solanum lycopersicum cultivar Vesuviano pizzo chloroplast, complete genome<br>
>MT811795.1 Solanum lycopersicum cultivar Vesuvio foglia riccia chloroplast, complete genome<br>
>MT811794.1 Solanum lycopersicum cultivar Vesuvio 2001 chloroplast, complete genome<br>
>MT811793.1 Solanum lycopersicum cultivar Pollena chloroplast, complete genome<br>
>MT811792.1 Solanum lycopersicum cultivar Piennolo giallo chloroplast, complete genome<br>
>MT811791.1 Solanum lycopersicum cultivar PDS chloroplast, complete genome<br>
>MT811790.1 Solanum lycopersicum cultivar Corbarino chloroplast, complete genome<br>
>MN218086.1 Solanum melongena isolate NN11 chloroplast, complete genome<br>
>MN218083.1 Solanum melongena isolate NN8 chloroplast, complete genome<br>
>MN218082.1 Solanum melongena isolate NN7 chloroplast, complete genome<br>
>MN218080.1 Solanum melongena isolate NN5 chloroplast, complete genome<br>
>MH283708.1 Solanum melongena voucher BM:Meeboonya et al. RM294 chloroplast, complete genome<br>
>KP117024.1 Solanum lycopersicum isolate TS-321 chloroplast, complete genome<br>
>MF818319.1 Solanum melongena chloroplast, complete genome<br>
>KY887588.1 Solanum lycopersicum chloroplast, complete genome<br>
>KY887587.1 Solanum lycopersicum chloroplast, complete genome<br>
>DQ231562.1 Solanum tuberosum chloroplast, complete genome<br>
>KM489055.2 Solanum nigrum chloroplast, complete genome<br>
>KM489056.2 Solanum tuberosum chloroplast, complete genome<br>
>KT375308.1 Solanum nigrum chloroplast, complete genome<br>
>DQ386163.2 Solanum tuberosum cultivar Desiree chloroplast, complete genome<br>
>HG975525.1 Solanum lycopersicum chloroplast, complete genome<br>
>KP331414.1 Solanum lycopersicum chloroplast, complete genome<br>
>DQ347959.1 Solanum lycopersicum cultivar LA3023 chloroplast, complete genome<br>
>JF772170.2 Solanum tuberosum isolate DM1-3-516-R44 chloroplast, complete genome<br>
>JF772171.1 Solanum tuberosum isolate RH89-039-16 chloroplast, complete genome<br>




## Next Steps:
Use the aligned genome sequence file to Build a Phylogenetic Tree using the following command in Terminal:

    iqtree -s aligned.fasta -m MFP -bb 1000 -nt AUTO


## Visualize the Tree using FigTree Software or online tools like iTOL:



## Summarize the Results:
(e.g., tree interpretation, GC% trends).
Create plots with Python (Matplotlib, Seaborn) etc.
