# Note pour la CFD — les 18 « recouvrements coplanaires » (MediumOffice ×6, LargeOffice ×12)

1. Diagnostic : ce n'est PAS un doublon. Chaque paire est une fenêtre en bande continue (z 0.9..2.5 m, toute la longueur du mur)
   et une porte (z 0..2.13 m) sur le même mur extérieur (même parent, même normale) ; recouvrement 1.0–1.1 m² (52–57 % de la porte).
2. Demande à E1 : renommer la classe (p. ex. `fenetre_recouvre_porte`) quand la paire est fenêtre × porte, et ne plus recommander
   « supprimer le doublon » (supprimer l'un ou l'autre perdrait une ouverture réelle).
3. Règle appliquée (validée par Paul le 05/10) : la porte reste entière ; la fenêtre est découpée en rectangles autour
   (bandes entre les portes + imposte au-dessus de chaque porte si elle dépasse TOL_AIRE / TOL_LARGEUR lues dans votre rapport) ;
   un éclat sous le seuil est supprimé et signalé ; un bilan par fenêtre (portes, surface de porte, vitrage avant/après).
4. Géométrie CFD uniquement : jamais appliquée aux seeds énergie (EUI et identité inchangées) ; un besoin énergie = un nouveau seed déclaré.
5. Résultat : 0 recouvrement fenêtre/porte restant (mesure indépendante), portes 6→6 et 12→12, 0 éclat, 0 refus.
6. OSM réparés : MediumOffice/MediumOffice_CFD_repare.osm et
   LargeOffice/LargeOffice_CFD_repare.osm, chacun avec son `.journal.json` (provenance sha256).
7. Code : lib/cfd/ouvertures.py (règle pure) + tools/cfd/repare_osm.py (coquille), à la pose.
