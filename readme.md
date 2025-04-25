Cursus Maître avec Django Rest Framework (DRF)

Phase 1 : Maîtriser Python
==========================
Jour 1. Programmation Avancée avec Python
-----------------------------------------
- Les variables et les Opérateurs
    - https://youtu.be/15Cn2UJZ7HQ
- Les conditions et les Boucles
    - https://youtu.be/t1EZcWaFyeg

Exercice:
Gukora fonctions isubiriza ijambo riri muri phrase idakoresheje fonction native replace()

Jour 2. Manipulation avancée des données
----------------------------------------
- Les listes et les fonctions y relatives (`sum`, `all`, `any`, `sorted`...)
    - https://youtu.be/0yySumZTxJ0
- Les chaînes de caractère:
    - https://youtu.be/9saytqA0J9A

Exercice:
1. script iguma ikora table de multiplication ibireka ari uko dushizemwo 0
2. script icapa carre yanditsemwo nombre de coté hagati
```
* * * * *
*       *
*   5   *
*       *
* * * * *
```

Jour 3. Les fichiers
--------------------
- Expression regulières
    - https://youtu.be/UQQsYXa1EHs
- Manipulation des fichiers
    - https://youtu.be/7U2RUtWz5Mo

Exercice:
Script itora fichier irimwo text igatanga iyindi fichier ariko ahari amajambo y'idome 5 iyasubira ari hagari y'utunyenyeri.

Akarorero:
Siko vyari vyifashe => siko * vyari * vyifashe

Jour 4. Les fichiers
--------------------
- Manipulation des dates
    - https://youtu.be/eirjjyP2qcQ
- Le module Path
    - https://youtu.be/p0Cy0LQ-sLw
    - https://youtu.be/TZkIud0u2C4
- [OPTIONNEL] logging
    - https://youtu.be/NRLSyyYv2N0

Exercice:
1. kora ama scripts akora ivyo
    - crea ama fichier 20: 1.txt, 2.txt,....
    - ayari pair yahindure extension abe .csv
    - ayari divisible par 3 yahe extexion .json
    - ayari < 10 yarenomme agire 0 kuntango 01.txt, 02.txt
    - ayari < 5 yahanagure
    - fichier ya 20 yandikemwo "OK NAHEJEJE"

2. script ifata fichier igatanga iyindi fihier ahari date hose ikahasubiriza imisi iba isigaye kugira ukwezi guhere

Akarorero:

15/04/2019 des flammes stylisées, rouge et or. =>  15e jours avant la fin de 04 2019 des flammes stylisées, rouge et or.

Jour 5. Exercices
-----------------
- [les boucles et les conditions](https://html-preview.github.io/?url=https://github.com/INGANZAMARUMPU/HOGI-Backend-Avance-2025/blob/main/renforcement_boucles.html)
- [les regexes et les fichiers](https://html-preview.github.io/?url=https://github.com/INGANZAMARUMPU/HOGI-Backend-Avance-2025/blob/main/renforcement_regex.html)

Jour 6. La Performance
----------------------
- Comprehensions et expressions Lambda (`map`, `filter`, `reduce`)
    - https://youtu.be/HQNiSfb795A
    - https://youtu.be/hUes6y2b--0
- Comprendre les itérateurs et générateurs
    - https://youtu.be/Zse3Zh6KqCc
- Le caching `functools.lru_cache()`
    - https://youtu.be/W6b6J1svbj8

Jour 7. Programmation Orientée Objet
------------------------------------
- `héritage multiple`, `encapsulation`, `polymorphisme`.
    - https://youtu.be/_8MS8jq23-g
    - https://youtu.be/29bZIPc94VU
    - https://youtu.be/DJEP8JTAb2U
- Attributs et méthodes statiques
    - https://youtu.be/45R-gynfbnw

Jour 8. Programmation Fonctionnelle
-----------------------------------
- Les closures.
    - https://youtu.be/oE0wFA13c2o
- Les décorateurs.
    - https://youtu.be/hcBhtCo07EQ
- [OPTIONNEL] la gestion avancée de memoire `gc` et `__slots__`
    - https://youtu.be/pVGujarYk9w
    - https://youtu.be/RtnzfYezHjo

Phase 2 : Maîtriser Django Rest Framework
=========================================
Jour 9. Django
--------------
- Les models et les requetes
- Django Admin

Jour 10. Django
---------------
- Django Admin en profondeur:
    filtres, actions, import-export, save_model, save_queryset, has_add_permission, list_prefetch_related, autocomplete_fields...

Jour 11. Django Rest Framework (DRF)
------------------------------------
- ModelViewset
- La Pagination
- Les Filtres
- Les actions
```python
@transaction.atomic
def destroy(self, request, *args, **kwargs):
    instance = self.get_object()
    for item in instance.factureitem_set.all():
        item.produit.quantite += item.quantite
        item.produit.save()
    instance.delete()
    return Response({"message": "Facture supprimée et produit ajusté"}, 200)

@transaction.atomic
@action(detail=False, methods=['POST'], serializer_class = MontantSerializer)
def augmenter(self, request):
    factures = self.get_queryset()
    serializer = self.get_serializer(data=request.data)
    serializer.is_valid(raise_exception=True)
    data = serializer.validated_data
    for facture in factures:
        facture.total = models.F('total') + data['montant']
        facture.save()

    factures = self.get_queryset()
    serializer = FactureSerializer(factures, many=True)
    return Response(serializer.data, 200)
```

Jour 12. Serialization
---------------------
- to_representation et les methods fields
- Les relations complexes : `OneToMany`, `ManyToMany`.
- [OPTIONNEL] GraphQL

Jour 13. Permissions
--------------------
- Validation avancée des données : regex, dates avec des formats dynamiques.
- JWT Authentication
- Gestion des permissions basée sur des rôles `(RBAC)`

Jour 14. La Securité
--------------------
- Protection contre les attaques : `CSRF`, `XSS` et `SQL injection`, `brute-force`, `Honeypot`
- Limitation des Requêtes: throttling

Jour 15. Les tests
------------------
- Les tests avec pytest
    - https://youtube.com/playlist?list=PLP1DxoSC17LZTTzgfq0Dimkm6eWJQC9ki

Phase 3 : La Performance
========================
Jour 16. Performance de l'API
-----------------------------
- Profilage et benchmarking
    - https://youtu.be/BZzb_Wpag_M

Jour 17. Caching
----------------
- Cache et optimisation des endpoints

Jour 18. Les taches
-------------------
- Mise en file d'attente des tâches avec Celery
    - https://youtu.be/y6FG-kKhGwA
- planification des tâches avec Celery
- [OPTIONNEL] Gestionnaire de taches personnalisé:
    - https://youtu.be/FCPBG6NqMmQ

Jour 19. SaaS
-------------
- [OPTIONNEL] Multitenancy avec django-tenants
    - https://youtu.be/uvaO85GbdzA

Jour 20. Django channels
------------------------
- [OPTIONNEL] Gestion des notifications et WebSockets

NB: Souvenez vous de faire un like pour chaque video que vous avez consultée
