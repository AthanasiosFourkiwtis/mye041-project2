# MYE-041 — Project 2: R-tree & Spatial Queries

Δεύτερη εργασία στο μάθημα **ΜΥΕ-041 Διαχείριση Σύνθετων Δεδομένων**, Τμήμα Μηχανικών Η/Υ & Πληροφορικής, Πανεπιστήμιο Ιωαννίνων.

## Περιεχόμενα

- `Rtree.py` — Κατασκευή R-tree με STR bulk loading
- `WindowQuery.py` — Window range queries
- `NNQuery.py` — k-Nearest neighbor queries
- `DistanceQuery.py` — Distance range queries
- `Beijing_restaurants.txt` — Δεδομένα εισόδου (συντεταγμένες εστιατορίων Πεκίνου)
- `windowRangeQueries.txt`, `distanceRangeQueries.txt`, `NNQueries.txt` — Αρχεία queries
- `rtree.csv`, `out_*.txt` — Παραδείγματα αρχείων εξόδου
- `Anafora2.pdf` — Αναφορά εργασίας
- `Assignment2.pdf` — Εκφώνηση

## Εκτέλεση

### Βήμα 1 — Κατασκευή του R-tree

Παίρνει το αρχείο σημείων και παράγει το `rtree.csv` (το serialized R-tree). **Πρέπει να τρέξει πρώτο** αφού τα queries βασίζονται στο `rtree.csv`:

```bash
python Rtree.py <input_points> <output_csv>
# παράδειγμα:
python Rtree.py Beijing_restaurants.txt rtree.csv
```

Στο τέλος τυπώνει στατιστικά (height, nodes per level, average MBR area).

### Βήμα 2 — Window Range Queries

Επιστρέφει όλα τα σημεία μέσα σε ορθογώνια παράθυρα:

```bash
python WindowQuery.py <rtree_csv> <queries_file> <output_file>
# παράδειγμα:
python WindowQuery.py rtree.csv windowRangeQueries.txt out_win.txt
```

### Βήμα 3 — Distance Range Queries

Επιστρέφει όλα τα σημεία εντός δεδομένης απόστασης από κάθε query σημείο:

```bash
python DistanceQuery.py <rtree_csv> <queries_file> <output_file>
# παράδειγμα:
python DistanceQuery.py rtree.csv distanceRangeQueries.txt out_dist.txt
```

### Βήμα 4 — k-NN Queries

Επιστρέφει τα `k` κοντινότερα σημεία για κάθε query σημείο. Δέχεται 1 επιπλέον όρισμα `k`:

```bash
python NNQuery.py <rtree_csv> <queries_file> <output_file> <k>
# παράδειγμα (k=5):
python NNQuery.py rtree.csv NNQueries.txt out_nn.txt 5
```

## Συγγραφέας

Αθανάσιος Φουρκιώτης (AM 4940)
