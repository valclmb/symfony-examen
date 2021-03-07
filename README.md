# Symfony - Examen

Pour travailler sur ce projet : 
- **créer un fork** du projet (sur la page [https://github.com/Dreeckan/exam-symfony](https://github.com/Dreeckan/exam-symfony), cliquer sur le bouton `fork`, en haut à droite de la page)
- Cloner **votre** projet (commande `git clone` par exemple)
- Créer une branche pour faire tout l'exam
- À la fin de l'examen, ajouter un dump (export de votre BdD depuis PhpMyAdmin) à la racine du projet (`exam-symfony.sql` par exemple)
- À la fin de l'examen, vous **devez** envoyer un zip de votre code sur Discord et vous **pouvez** faire une PR à destination du projet d'origine (afin de faciliter mes retours pour la correction)

**1 point bonus** peut être gagné si votre code est valide PSR-12 et PSR-4 (3 erreurs autorisées au total).

La durée prévue est d'environ 4h. Des points peuvent être perdus pour le retard du rendu :
- 1 point si le rendu est fait après 19h
- 2 point si le rendu est fait après 23h59

Liste des exercices
1. Contrôleurs et routes (2 points)
2. Vues avec Twig (3 points)
3. Doctrine et la base de données (4 points)
4. Formulaires et entités (4 points)
  4.1. Formulaire de contact
  4.2. Validation
5. Créer des services (5 points)
  5.1. Un lanceur de dés
    - Lance x d 20
    - Lance x d 100
    - Lance x d quelconque
  5.2. Résoudre une action
  5.3. Tester
6. Questions de cours (2 points)
  x4 ?
   
## 1. Contrôleurs et routes (2 points)

- Créer un controller : 
  - [ ] nommé `DefaultController`, 
  - [ ] contenant une action `index`,
  - [ ] dont le chemin est `/`
  - [ ] créer le template associé (`default/index.html.twig`) (le laisser vide, il sera rempli dans l'exercice 2)
  
- Créer une deuxième route :
  - [ ] dont l'action s'appelle `contact`
  - [ ] dont le chemin est `/contact`
  - [ ] créer le template associé `default/contact.html.twig` (le laisser vide, il sera rempli dans les exercices 2 et 4)
  
## 2. Vues avec Twig (3 points)

- [ ] Créer un template `default/layout.html.twig` héritant de `base.html.twig`
  - [ ] Y ajouter les feuilles de style et les javascripts (version "Bundle") de [Boostrap 4](https://getbootstrap.com/docs/4.6/getting-started/introduction/)
  - [ ] Créer un bloc `header`, un bloc `footer` et un bloc `content`
  - [ ] Ajouter une div **autour** du bloc content, avec la classe `container-fluid`
  - [ ] Dans `footer`, ajouter le contenu `<div>Un site tout droit libre de tous droits</div>`
  - Dans `default/index.html.twig` :
    - [ ] Adapter votre vue pour hériter de `layout.html.twig` et utiliser ses blocs
    - [ ] Dans le `header` ajouter le contenu `<h1>un titre magnifique</h1>`
    - [ ] À l'aide d'un [filtre Twig](https://twig.symfony.com/doc/), faire en sorte que chaque mot de ce titre ait une majuscule
    - [ ] Vérifier que les éléments sont bien affichés
  - Dans `default/contact.html.twig` :
    - [ ] Adapter votre vue pour hériter de `layout.html.twig` et utiliser ses blocs
    - [ ] Dans le `header` ajouter le contenu `<h1>Nous Contacter</h1>`
    - [ ] Dans le contenu, ajouter le texte : `Nous sommes actuellement le : ` et afficher la date du jour (avec la fonction Twig `date()`) et l'afficher au format `d/m/Y H:i:s` (avec le filtre Twig `date`) (s'il y a un décalage d'une ou deux heures, peu importe)
    - [ ] Vérifier que les éléments sont bien affichés
  
## 3. Doctrine et la base de données (4 points)

## 3.0. Configuration

- [ ] Vérifier / mettre à jour la configuration de Doctrine et de la base de données (BdD)
- [ ] Créer la BdD

## 3.1. Entité
- [ ] Créer une entité `Contact` avec les propriétés suivantes :
  - [ ] `id`, integer, non null, auto increment
  - [ ] `email`, string (128), non null
  - [ ] `subject`, string (255), non null
  - [ ] `message`, text, non null
  - [ ] `created_at`, datetime
- [ ] Faire en sorte que la propriété prenne la date et heure du jour lors de la création d'un nouvel objet `Contact` (objet `DateTime` contenant la date et l'heure de création de l'objet)
- [ ] Créer la table correspondante dans votre BdD

## 3.2. Enregistrement de données

- [ ] Dans l'action `contact`, au chargement de la page, créer une instance de `Contact` avec les données suivantes :
  - `email` : `test@test.com`
  - `subject` : `Ceci est un test`
  - `message` : `Un message de test, pouvant être long, ou non. Celui-ci ne l'est pas :) .`
- [ ] Sauvegarder cette donnée dans la BdD
- [ ] Vérifier le fonctionnement

## 3.3. Récupération de données

- [ ] Dans l'action `index`, récupérer toutes les entrées de votre table `contact`
  - [ ] Les afficher dans un tableau HTML dans la vue `default/index.hml.twig`
- [ ] Dans le repository correspondant, écrire une méthode renvoyant tous les objets `Contact` dont le champ email est `test@test.com`


## 4. Formulaires et entités (4 points)