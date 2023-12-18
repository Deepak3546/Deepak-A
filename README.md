def find_orfs(sequence, min_length=50):
    orfs = []
    start_codon = "ATG"
    stop_codons = ["TAA", "TAG", "TGA"]

    for i in range(len(sequence)):
        if sequence[i:i + 3] == start_codon:
            for j in range(i + 3, len(sequence), 3):
                codon = sequence[j:j + 3]
                if codon in stop_codons:
                    if j - i + 3 >= min_length:
                        orfs.append(sequence[i:j + 3])
                    break

    return orfs
