---
title: "Proc&#233;dure pas &#224; pas&#160;: G&#233;n&#233;rateur de profils XSLT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Proc&#233;dure pas &#224; pas&#160;: G&#233;n&#233;rateur de profils XSLT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le Générateur de profils XSLT crée des rapports de performances XSLT détaillés qui vous permettent de mesurer, d'évaluer et de cibler les problèmes liés aux performances dans le code XSLT.Le Générateur de profils XSLT inclut des conseils utiles pour les optimisations de feuille de style XSL et XSLT.Pour les applications XSLT qui demandent des performances maximales, cet outil peut être essentiel.  
  
## Composants requis  
 Les procédures dans la procédure pas à pas suivante nécessitent Visual Studio 2010 et le .NET Framework version 4.0.Le Générateur de profils XSLT est uniquement disponible si Microsoft Visual Studio Team System avec les outils de profilage est installé.  
  
### Créer le rapport de performances  
  
1.  Ouvrez un document XSLT dans Visual Studio.  
  
2.  Cliquez sur l'option **Profil XSLT** qui est disponible dans le menu XML.  
  
3.  Fournissez un document XML d'entrée.Si un document XML n'est pas déjà ouvert, vous êtes invité à entrer le fichier.  
  
4.  L'analyse démarre, et une barre de progression affiche la progression dans l'éditeur.  
  
5.  La sortie XSLT est visible dans le panneau de sortie.  
  
6.  Au terme d'une session de performance, examinez le rapport de performances.Les données enregistrées dans un rapport de performances vous permet d'afficher et d'analyser les performances XSLT.  
  
### Obtenir toutes les vues disponibles  
  
1.  Cliquez sur la liste déroulante **Affichage actuel** pour obtenir toutes les vues disponibles.  
  
2.  Sélectionnez l'option **Mode Résumé** dans la liste déroulante **Affichage actuel**.Par défaut, un rapport de performances est affiché dans le **Mode Résumé**.Cette vue sert de point de départ pour déterminer les problèmes de performances avec les documents XSLT.Le **Mode Résumé** répertorie les points de données suivants :  
  
    -   Majorité des fonctions appelées  
  
    -   Fonctions faisant le plus de travail individuel  
  
    -   Fonctions les plus longues à exécuter  
  
3.  Par défaut, il y a trois colonnes pour chaque point de données : le nom de la fonction, le nombre d'appels en valeur absolue, et une valeur en pourcentage de la fonction nommée par rapport au nombre total d'appels de fonction.À partir de chaque point de données du **Mode Résumé**, vous pouvez accéder à des vues plus détaillées en cliquant avec le bouton droit sur les points de données de la fonction.  
  
4.  Sélectionnez l'option **Mode Fonctions** dans la liste déroulante **Affichage actuel**.Le **Mode Fonctions** répertorie les fonctions appelées lors du profilage.Vous pouvez trier les données en cliquant sur un nom de colonne.Les colonnes affichées par défaut sont les suivantes :  
  
    -   **Nom de la fonction**  
  
    -   **Temps inclusif écoulé**  
  
    -   **Temps exclusif écoulé**  
  
    -   **Temps inclusif d'application**  
  
    -   **Temps exclusif d'application**  
  
    -   **Nombre d'appels**  
  
5.  Toutes les colonnes d'heure sont affichées en valeurs absolues et en pourcentages.Le terme **Exclusif** fait référence à la durée totale de l'exécution d'une fonction, à l'exclusion de la durée d'exécution d'autres fonctions appelées pendant l'exécution de cette fonction.  
  
6.  Le terme **Inclusif** fait référence à la durée totale de l'exécution d'une fonction, y compris la durée d'exécution de toutes les fonctions appelées pendant l'exécution de cette fonction et l'appel d'autres fonctions par ces fonctions appelées.  
  
### Sélectionner la vue Appelant\/Appelé  
  
1.  Sélectionnez la vue **Appelant\/Appelé** dans la liste déroulante **Affichage actuel**.  
  
2.  La vue **Appelant\/Appelé** comprend les trois parties distinctes suivantes :  
  
    -   **Fonctions qui ont appelé** : toutes les fonctions qui ont appelé une fonction particulière sont répertoriées dans la partie supérieure de la vue.  
  
    -   **Fonction actuelle** : la fonction particulière appelée apparaît dans la partie centrale de la vue.  
  
    -   **Fonctions qui ont été appelées par** : toutes les fonctions qui ont été appelées par la fonction particulière sont répertoriées dans la partie inférieure de la vue.  
  
3.  Si une fonction nommée `SyncToNavigator` apparaît dans la partie centrale de la vue, toutes les fonctions qui ont appelé la fonction `SyncToNavigator` s'affichent dans la partie supérieure de la vue et toutes les fonctions appelées par la fonction `SyncToNavigator` s'affichent dans la partie inférieure de la vue.  
  
4.  Vous pouvez modifier la fonction dans la partie centrale de la vue en double\-cliquant sur une des fonctions répertoriées dans les autres parties de la vue.La vue est mise à jour automatiquement pour refléter les modifications.  
  
5.  Vous pouvez aussi trier les données en cliquant sur les noms de colonnes.  
  
### Sélectionner la vue de l'arborescence des appels  
  
1.  Sélectionnez **Vue de l'arborescence des appels** dans la liste déroulante **Affichage actuel**.Cette vue est une arborescence de l'exécution du programme.  
  
2.  La**Vue de l'arborescence des appels** affiche la racine de l'arborescence en tant que nom de processus.Les fonctions sont les nœuds de l'arborescence.Cette vue vous permet d'explorer des traces d'appels spécifiques et d'analyser les traces qui affectent le plus les performances.La vue est semblable à la **Vue de la pile des appels** disponible lors du débogage.En plus des colonnes dans le **Mode Fonctions**, dans la **Vue de l'arborescence des appels**, une colonne supplémentaire indique le **Nom du module**.  
  
3.  Sélectionnez **Marques** dans la liste déroulante **Affichage actuel**.  
  
4.  Avec le Générateur de profils SLT, des marques apparaissent dans le flux de collection de données avec un commentaire associé.Les marques sont emplacements dans le code qui ont des compteurs.Lorsque vous indiquez au Générateur de profils SLT de collecter des compteurs de performance XSLT, ceux\-ci sont collectés chaque fois que l'une de ces marques est exécutée.Les données sont affichées dans une table qui contient l'**ID de marque**, le **Nom de marque** \(**Programme de démarrage**, **Programme de fin**\) et l'**Horodatage**.Les marques ne sont pas regroupées et apparaissent dans l'ordre chronologique dans la **Vue des marques** du rapport de performances.  
  
### Sélectionner des modules dans l'affichage actuel  
  
1.  Sélectionnez **Modules** dans la liste déroulante **Affichage actuel**.  
  
2.  La vue de modules est une liste plate de toutes les fonctions agrégées au niveau du module.Développez ou réduisez le nom du module pour afficher ou fermer la vue des données de performances du module.Vous pouvez trier les données en cliquant sur un nom de colonne.Par défaut, **Temps inclusif écoulé**, **Temps exclusif écoulé**, **Temps inclusif d'application**, **Temps exclusif d'application** et **Nombre d'appels** comprennent des valeurs absolues et des pourcentages.  
  
3.  Sélectionnez **Processus** dans la liste déroulante **Affichage actuel**.  
  
4.  La vue de processus affiche une table qui inclut l'**ID de processus**, le **Nom du processus**, l'**Heure de début** et l'**Heure de fin**.Vous pouvez trier les données en cliquant sur les noms de colonnes.  
  
## Voir aussi  
 [Procédure pas à pas : utilisation de XSLT Hierarchy](../xml-tools/walkthrough-using-xslt-hierarchy.md)