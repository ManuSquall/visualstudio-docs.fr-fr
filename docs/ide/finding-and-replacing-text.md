---
title: "Recherche et remplacement de texte | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.find"
  - "vs.findreplacecontrol"
  - "vs.findreplace.findsymbol"
  - "vs.findreplace.symbol"
  - "findresultswindow"
  - "vs.findreplace.quickreplace"
  - "vs.findsymbol"
  - "vs.findinfiles"
  - "vs.findresults1"
  - "vs,findsymbolwindow"
  - "vs.findreplace.quickfind"
  - "vs.lookin"
  - "vs.replace"
helpviewer_keywords: 
  - "find"
  - "rechercher et remplacer"
  - "Rechercher dans les fichiers (boîte de dialogue)"
  - "rechercher du texte"
  - "find, symbole"
  - "find, texte"
  - "replace"
  - "Remplacer (boîte de dialogue)"
  - "Remplacer dans les fichiers (boîte de dialogue)"
  - "remplacer du texte"
  - "recherches de texte"
  - "recherches de texte, rechercher et remplacer du texte"
  - "texte, rechercher et remplacer"
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# Recherche et remplacement de texte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez rechercher et remplacer du texte dans l'éditeur de code Visual Studio, et certaines fenêtres de sortie basées sur du texte telles que les fenêtres **Résultats de recherche**, en utilisant le contrôle **Rechercher et remplacer** ou **Rechercher\/Remplacer dans les fichiers**.  Vous pouvez également utiliser les fonctions de recherche et de remplacement dans certaines fenêtres du concepteur, telles que le concepteur XAML et le concepteur Windows Forms, ainsi que les fenêtres Outil  
  
 Vous pouvez limiter les recherches au document actif, à la solution actuelle ou à un ensemble de dossiers personnalisé.  Vous pouvez également spécifier un ensemble d'extensions de nom de fichier pour les recherches multifichier.  Vous pouvez personnaliser la syntaxe de recherche à l'aide d'expressions régulières .NET.  
  
 Pour rechercher et remplacer des expressions régulières, consultez [Utilisation d'expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
> [!TIP]
>  La zone **Rechercher\/Commande** reste disponible en tant que contrôle de barre d'outils, mais n'est plus visible par défaut.  Vous pouvez afficher la zone **Rechercher\/Commande** en sélectionnant **Ajouter ou supprimer des boutons** dans la barre d'outils **Standard**, puis en sélectionnant **Rechercher**.  Pour plus d'informations, consultez [Zone Rechercher\/Commande](../ide/find-command-box.md).  
  
## Rechercher et remplacer un contrôle  
 Le contrôle **Rechercher et remplacer** s'affiche dans l'angle supérieur droit de la fenêtre de l'éditeur de code.  Le contrôle **Rechercher et remplacer** met immédiatement en surbrillance chaque occurrence de la chaîne de recherche donnée dans le document actif.  Vous pouvez passer d'une occurrence à une autre en sélectionnant le bouton **Suivant** ou le bouton **Précédent** sur le contrôle de recherche.  
  
 Vous pouvez accéder aux options de remplacement en sélectionnant le bouton en regard de la zone de texte **Rechercher**.  Pour effectuer un remplacement à la fois, sélectionnez le bouton **Suivant** en regard de la zone de texte **Remplacer**.  Cliquez sur **Remplacer tout** pour remplacer toutes les occurrences en une seule fois.  
  
 Pour modifier la couleur de surbrillance des correspondances, choisissez le menu **Outils**, sélectionnez **Options**, choisissez **Environnement**, puis sélectionnez **Polices et couleurs**.  Dans la liste **Afficher les paramètres de**, sélectionnez **Éditeur de texte**, puis dans la liste **Éléments d'affichage**, sélectionnez **Rechercher un surlignage \(extension\)**.  
  
### Recherche dans les fenêtres Outil  
 Vous pouvez utiliser le contrôle **Rechercher** dans les fenêtres de code ou de texte, telles que les fenêtres **Sortie** et les fenêtres **Résultats de recherche**, en sélectionnant **Rechercher et remplacer** dans le menu **Modifier** ou \(CTRL\+F\).  
  
 Une version du contrôle Rechercher est également disponible dans certaines fenêtres Outil.  Par exemple, vous pouvez maintenant filtrer la liste de contrôles dans la fenêtre **Boîte à outils** en entrant du texte dans la zone de recherche.  Les autres fenêtres outil qui vous permettent à présent de rechercher leur contenu sont **Explorateur de solutions**, la fenêtre **Propriétés**, et **Team Explorer**, entre autres.  
  
## Rechercher\/remplacer dans les fichiers  
 L'option **Rechercher\/remplacer dans les fichiers** fonctionne comme le contrôle **Rechercher et remplacer**, mais vous pouvez définir une portée de recherche.  Non seulement vous pouvez rechercher le fichier actif ouvert dans l'éditeur, mais vous pouvez également rechercher tous les documents ouverts, la solution, le projet actuel et les jeux de dossiers sélectionnés.  Vous pouvez également effectuer une recherche en fonction de l'extension de nom de fichier.  Pour accéder à la boîte de dialogue **Rechercher\/Remplacer dans les fichiers**, sélectionnez **Rechercher et remplacer** dans le menu **Edition** \(ou CTRL\+MAJ\+F\).  
  
 Lorsque vous sélectionnez **Rechercher tout**, une fenêtre **Résultats de la recherche** s'ouvre et affiche les résultats de la recherche.  La sélection d'un résultat dans la liste affiche le fichier associé et met la correspondance en surbrillance.  Si le fichier n'est pas déjà ouvert pour modification, il sera ouvert dans un onglet d'aperçu dans le côté droit de l'onglet.  Vous pouvez utiliser le contrôle **Rechercher** pour effectuer des recherches dans la liste **Résultats de recherche**.  
  
### Création de jeux de dossiers de recherche personnalisés  
 Vous pouvez définir une étendue de recherche en sélectionnant le bouton **Choisir des dossiers de recherche** \(il ressemble à **…**\) en regard de la zone **Regarder dans**.  Dans la boîte de dialogue **Choisir des dossiers de recherche**, vous pouvez spécifier un ensemble de dossiers dans lequel effectuer la recherche, et vous pouvez enregistrer la spécification afin que vous puissiez la réutiliser ultérieurement.  Vous pouvez spécifier des dossiers sur un ordinateur distant uniquement si vous avez mappé son lecteur sur l'ordinateur local.  
  
### Création d'ensembles de composants personnalisés  
 Vous pouvez définir des jeux de composants en fonction de votre étendue de recherche en sélectionnant le bouton **Modifier un jeu de composants personnalisés** en regard de la zone **Regarder dans**.  Vous pouvez spécifier des composants .NET ou COM installés, des projets Visual Studio inclus dans votre solution ou une bibliothèque d'assemblys ou de types \(.dll, .tlb, .olb, .exe ou .ocx\).  Pour rechercher des références, sélectionnez la case **Regarder dans les références**.  
  
## Voir aussi  
 [Utilisation d'expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)