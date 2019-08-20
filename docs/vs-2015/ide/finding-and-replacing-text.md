---
title: Recherche et remplacement de texte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.find
- vs.findreplacecontrol
- vs.findreplace.findsymbol
- vs.findreplace.symbol
- findresultswindow
- vs.findreplace.quickreplace
- vs.findsymbol
- vs.findinfiles
- vs.findresults1
- vs,findsymbolwindow
- vs.findreplace.quickfind
- vs.lookin
- vs.replace
helpviewer_keywords:
- text searches
- Replace in Files dialog box
- find, text
- Find in Files dialog box
- find
- text searches, finding and replacing text
- Replace dialog box
- text, finding and replacing
- find, symbol
- find and replace
- replace
- find text
- replacing text
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 51d361bf74fb1181c64e5299b0925c262f185e9b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63426335"
---
# <a name="finding-and-replacing-text"></a>Finding and Replacing Text
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez rechercher et remplacer du texte dans l’éditeur de code Visual Studio, et certaines fenêtres de sortie basées sur du texte telles que les fenêtres **Résultats de la recherche**, en utilisant le contrôle **Rechercher et remplacer** ou **Rechercher/Remplacer dans les fichiers**. Vous pouvez également utiliser les fonctions de recherche et de remplacement de certaines fenêtres de concepteur, par exemple du concepteur XAML et du concepteur Windows Forms, ainsi que les fenêtres d’outils.  
  
 Vous pouvez limiter les recherches au document actif, à la solution actuelle ou à un ensemble de dossiers personnalisé. Vous pouvez également spécifier un ensemble d’extensions de nom de fichier pour les recherches multifichiers. Vous pouvez personnaliser la syntaxe de recherche à l’aide d’expressions régulières .NET.  
  
 Pour rechercher et remplacer des expressions régulières, consultez [Utilisation d’expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
> [!TIP]
> La zone **Rechercher/Commande** reste disponible en tant que contrôle de barre d’outils, mais n’est plus visible par défaut. Vous pouvez afficher la zone **Rechercher/Commande** en choisissant **Ajouter ou supprimer des boutons** dans la barre d’outils **Standard**, puis en choisissant **Rechercher**. Pour plus d’informations, consultez [Zone Rechercher/Commande](../ide/find-command-box.md).  
  
## <a name="find-and-replace-control"></a>Contrôle Rechercher et remplacer  
 Le contrôle **Rechercher et remplacer** s’affiche dans le coin supérieur droit de la fenêtre de l’éditeur de code. Le contrôle **Rechercher et remplacer** met immédiatement en surbrillance chaque occurrence de la chaîne de recherche donnée dans le document actif. Vous pouvez passer d’une occurrence à une autre en choisissant le bouton **Suivant** ou **Précédent** sur le contrôle de recherche.  
  
 Vous pouvez accéder aux options de remplacement en choisissant le bouton en regard de la zone de texte **Rechercher**. Pour effectuer un remplacement à la fois, choisissez le bouton **Suivant** en regard de la zone de texte **Remplacer**. Pour remplacer toutes les occurrences en une seule fois, choisissez le bouton **Remplacer tout**.  
  
 Pour modifier la couleur de surbrillance des correspondances, choisissez le menu **Outils**, sélectionnez **Options**, puis choisissez **Environnement** et sélectionnez **Polices et couleurs**. Dans la liste **Afficher les paramètres de**, sélectionnez **Éditeur de texte**, puis, dans la liste **Éléments d’affichage**, sélectionnez **Rechercher un surlignage (extension)** .  
  
### <a name="searching-tool-windows"></a>Recherche dans les fenêtres d’outils  
 Vous pouvez utiliser le contrôle **Rechercher** dans les fenêtres de code ou de texte, telles que les fenêtres **Sortie** et les fenêtres **Résultats de la recherche**, en choisissant **Rechercher et remplacer** dans le menu **Edition** ou (Ctrl+F).  
  
 Une version du contrôle Rechercher est également disponible dans certaines fenêtres d’outils. Par exemple, vous pouvez maintenant filtrer la liste des contrôles dans la fenêtre **Boîte à outils** en entrant du texte dans la zone de recherche. D’autres fenêtres d’outils qui vous permettent à présent de rechercher leur contenu incluent l’**Explorateur de solutions**, la fenêtre **Propriétés** et **Team Explorer**, entre autres.  
  
## <a name="findreplace-in-files"></a>Rechercher/Remplacer dans les fichiers  
 L’option **Rechercher/Remplacer dans les fichiers** fonctionne comme le contrôle **Rechercher et remplacer**, à ceci près que vous pouvez définir une étendue de recherche. Non seulement vous pouvez rechercher dans le fichier actif ouvert dans l’éditeur, mais vous pouvez également rechercher dans tous les documents ouverts, la solution complète, le projet actuel et les jeux de dossiers sélectionnés. Vous pouvez également effectuer une recherche basée sur une extension de nom de fichier. Pour accéder à la boîte de dialogue **Rechercher/Remplacer dans les fichiers**, choisissez **Rechercher et remplacer** dans le menu **Edition** (ou Ctrl+Maj+F).  
  
 Lorsque vous choisissez **Rechercher tout**, une fenêtre **Résultats de la recherche** s’ouvre et répertorie les résultats de la recherche. Si vous sélectionnez un résultat dans la liste, le fichier associé est affiché et la correspondance est mise en surbrillance. Si le fichier n’est pas encore ouvert pour modification, il est ouvert dans un onglet d’aperçu dans la partie droite de la zone de configuration des onglets. Vous pouvez utiliser le contrôle **Rechercher** pour effectuer des recherches dans la liste **Résultats de la recherche**.  
  
### <a name="creating-custom-search-folder-sets"></a>Création de jeux de dossiers de recherche personnalisés  
 Vous pouvez définir une étendue de recherche en choisissant le bouton **Choisir des dossiers de recherche** (il ressemble à **...** ) en regard de la zone **Regarder dans**. Dans la boîte de dialogue **Choisir des dossiers de recherche**, vous pouvez spécifier un jeu de dossiers dans lequel effectuer la recherche et vous pouvez enregistrer la spécification afin de pouvoir la réutiliser ultérieurement. Vous pouvez spécifier des dossiers sur un ordinateur distant uniquement si vous avez mappé son lecteur à l’ordinateur local.  
  
### <a name="creating-custom-component-sets"></a>Création d’ensembles de composants personnalisés  
 Vous pouvez définir des jeux de composants comme étendue de recherche en choisissant le bouton **Modifier un jeu de composants personnalisés** en regard de la zone **Regarder dans**. Vous pouvez spécifier des composants .NET ou COM installés, des projets Visual Studio inclus dans votre solution ou toute bibliothèque d’assemblys ou de types (.dll, .tlb, .olb, .exe ou .ocx). Pour rechercher des références, cochez la case **Regarder dans les références**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)
