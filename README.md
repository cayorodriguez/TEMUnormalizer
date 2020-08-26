# TEMUnormalizer
Baseline term normalizer to find Snomed and CIE-10 codes
Two very simple strategies for now:
- Direct Match from dictionary
- Fuzzy match using the rapidfuzz library (https://github.com/maxbachmann/rapidfuzz)

-In code, there is a third strategy using a w2v matrix for soft cosine indexing, but is not operative

python TEMUnormalizer.py -h
Usage: TEMUnormalizer.py [options]

Options:
  -h, --help            show this help message and exit
  -d REFERENCE_DICT, --dictionary=REFERENCE_DICT
                        tab-separated (term to code) file to create reference
                        dictionary from
                        
  -f FILEOUT, --fileout=FILEOUT
                        output file, tab-separated values extension (.tsv)
                        
  -t TERMLIST, --terms=TERMLIST
                        file with term list to normalize, one per line
                        
  -a BRAT, --ann=BRAT    treat input file as brat .ann file with term list to
                        normalize, one per line
                        
  -e ENTITIES, --entities=ENTITIES
                        give a list (comma-separated) of names of entities to
                        normalize. Otherwise, will try to normalize everything
                        
e.g.: python TEMUnormalizer.py -d./tsv_dictionaries/SpanishSnomed.tsv 
  -f  normalized_list_snomed_from_ann.tsv 
  -t S0004-06142005000200004-1.ann 
 -a 1 
 -e ENFERMEDAD,FARMACOS,FARMACOS-2
  -u UMBRAL, --umbral=UMBRAL threshold for fuzzy search (default 93)
