# Εργασία στο Gephi



## Μέρος Α: Δημιουργία δικτύου χρηστών

Αρχικά, με τον Αλγόρυθμο 1 του Παρατήματος δημιουργήκαν τα _csv_ αρχεία και για τα τρία θέματα.

Έπειτα με την διαδικασία που περιγράφεται στην εκφώνηση της άσκησης δημιουργήθηκαν τα αρχεία _gdf_.

Τέλος, με τη βοήθεια του λογισμικού _Gephi_ υλοποιήθηκε η αναπαράσταση του γράφου κάθε θέματος.

Στις _Εικόνες 1 έως 3_ αναπαρίστατε ο γράφος κάθε θέματος, όπου,
 * το χρώμα των κόμβων αντιστηχεί στο _Modularity class_,
 * το μέγεθος των κόμβων στο _Centrality Degree_,
 * το μέγεθος της κάθε λεζάντας κάθε κόμβου στο _Betweeness Centrality_ και 
 * το χρώμα της κάθε λεζάντας στο _PageRank_.


![alt text](png/Evolution_Preview.png)

_Εικόνα 1_: Γράφος δικτύου χρηστών του θέματος _Evolution_.


![alt text](png/GayMarriage_Preview.png)

_Εικόνα 2_: Γράφος δικτύου χρηστών του θέματος _GayMarriage_.


![alt text](png/GlobalWarming_Preview.png)

_Εικόνα 3_: Γράφος δικτύου χρηστών του θέματος _GlobalWarming_.

 

## Μέρος Β: Δημιουργία δικτύου λέξεων

Ομοίως με το Μέρος Α, με τον Αλγόρυθμο 1 του Παρατήματος δημιουργήκαν τα _csv_ αρχεία και για τα τρία θέματα.

Έπειτα, με τη βοήθεια του λογισμικού _RapidMiner_ και ακολουθόντας τη διαδικασία που φαίνεται στις _Εικόνες 4 και 5_
δημιουργήθηκε η λίστα των _3-grams_.

H διαδικασία της _Εικόνας 4_ είναι η κύρια και αποτελείτε από τα εξής βήματα:
1. _Read CSV_, εισάγωγή των δεδομένων _Username_ και _post_ από το αρχείο _csv_, ως _nominal_ και _text_ αντίστοιχα.
1. _Process Documents from Data_, επεξεργασία του κειμένου κάθε _post_ ως εξής:
   1. _Tokenize_, διαχωρισμός των λέξεων,
   1. _Stem (Snowball)_, εφαρμογή του αλγορίθμου _Snowball_ σε κάθε λέξη,
   1. _Filter Stopwords (English)_, αφαιρεση των σημείων στίξης,
   1. _Filter Tokens (by Length)_, αφαίρεση των λέξεων με λιγότερα από 4 ή περισσότερα από 25 γράμματα,
   1. _Generate n-Grams (Terms)_, δημιουργία 3-grams.
1. _WordList to Data_, μετατροπή της λίστας σε μορφή δεδομένων,
1. _Select Attributes_, απομόνωνση των _3-grams_ από τα δεδομένα,
1. _Write CSV_, εγγραφή των _3-grams_ σε αρχείο "csv".



![alt text](png/Process.png)

_Εικόνα 4_: Η κύρια διαδικασία για τη δημιουργία της λίστα των _3-grams_.


![alt text](png/Process%20document%20from%20data.png)

_Εικόνα 5_: Η διαδικασία της επεξεργασίας του κάθε post, για τη δημιουργία της λίστα των _3-grams_.


Στη συνέχεια, ειγάγεται το αρχείο _csv_ στον Αλγόριθμο 2 του Παραρτήματος, όπου αφαιρούνται οι λέξεις που περιέχουν 
περισσότερες από 2 συνεχόμενες φορές το ίδιο γράμμα και δημιουργείται το αρχείο _csv_ της μορφής _"Source;Target"_ 
σύμφωνα με την εκφώνηση.

Έπειτα, δημιουργήθηκαν τα αρχεία _gdf_ και με τη βοήθεια του λογισμικού _Gephi_ υλοποιήθηκε η αναπαράσταση του γράφου 
για τα θέματα _GayMarriage_ και _GlobalWarming_. Για αδιεκρίνιστο λόγο και ενώ ακολουθήθηκε η ίδια διαδικασία, το 
_Gephi_ εμφάνιζε σφάλμα κατά τη φόρτωση του αρχείου _gdf_, το οποίο δημιουρθήκε επίσης από το _Gephi_.

Στις _Εικόνες 6 και 7_ αναπαρίστατε ο γράφος του θέματας _GayMarriage_ και _GlobalWarming_, αντίστοιχα, όπου,
 * το χρώμα των κόμβων αντιστηχεί στο _Modularity class_,
 * το μέγεθος των κόμβων στο _Centrality Degree_,
 * το μέγεθος της κάθε λεζάντας κάθε κόμβου στο _Betweeness Centrality_ και 
 * το χρώμα της κάθε λεζάντας στο _PageRank_.

Λόγο του μεγάλου πλήθους κόμβων και ακμών ήταν ανέφυκτη η επεξεργασια της διάταξης.

![alt text](png/GayMarriage_Preview_b.png)

_Εικόνα 6_: Γράφος δικτύου λέξεων του θέματος _GayMarriage_.


![alt text](png/GlobalWarming_Preview_b.png)

_Εικόνα 7_: Γράφος δικτύου λέξεων του θέματος _GlobalWarming_.


## Παράρτημα

### Αλγόριθμος 1

```
def export_csv(dataset, output_directory=''):
    '''From a data set "txt" file, exports the "cvs" files for part A and B of the exercise.
    For the part A, the format of the file is "Source;Target;Weight".
    For the part B, the format of the file is "Username;post".

    :param dataset: the name of the "txt" file is "{dataset}.txt"
    :param output_directory: the folder to be saved the "csv" files
    :return: "{dataset}_a.csv" and "{dataset}_b.csv" files
    '''

    file = 'Arguments/{}.txt'.format(dataset)
    n = 0
    line_is_text = False
    first_line = True
    with open(file, 'r') as rp, \
            open('{}{}_a.csv'.format(output_directory, dataset), 'w') as wp1, \
            open('{}{}_b.csv'.format(output_directory, dataset), 'w') as wp2:

        if first_line:
            wp1.write('Source;Target;Weight\n')
            wp2.write('Username;post\n')
            first_line = False

        for line in rp:
            if '===NEW ARGUMENT==' in line:
                if n > 0:
                    if names.count(';') == 2:
                        wp1.write('{}{}\n'.format(names, n))
                names = ''
                n = 0

            elif '{' in line:
                n += 1
                if previous_line not in names:
                    names += previous_line + ';'
                latest_name = previous_line
                line_is_text = True
            elif line_is_text:
                wp2.write('{};{}\n'.format(latest_name, line.strip()))
                line_is_text = False

            previous_line = line.strip()

        if names.count(';') == 2:
            wp1.write('{}{}\n'.format(names, n))
```

### Αλγόριθμος 2

```
def ngrams_csv(dataset, output_directory):
    '''From the exported "csv" file of the RapidMiner exports a "csv" file.
    The format of the "csv" is "Source;Target" and the content as described in part B of the exercise.

    :param dataset: the name of the imported "csv" file is "{dataset}_rpm.csv"
    :param output_directory: the folder to be saved the "csv" file
    :return: "{dataset}_rmp_b.csv" file
    '''

    file = 'csv/{}_rmp.csv'.format(dataset)
    with open(file, 'r') as rp, \
        open('{}{}_rmp_b.csv'.format(output_directory, dataset), 'w') as wp:

        wp.write('Source;Target\n')
        for line in rp:
            c = line.count('_')
            words = line.strip().split('_')
            
            if search(r'(.)\1{2,}', words[0]) is not None:
                continue
                
            if c == 1 and search(r'(.)\1{2,}', words[1]) is None:
                wp.write('{};{}\n'.format(words[0], words[1]))
                
            elif c == 2:
                if search(r'(.)\1{2,}', words[2]) is None:
                    wp.write('{};{}\n'.format(words[0], words[2]))
                if search(r'(.)\1{2,}', words[1]) is None:
                    wp.write('{};{}\n'.format(words[1], words[2]))
```
