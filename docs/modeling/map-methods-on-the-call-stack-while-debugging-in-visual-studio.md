---
title: Mapper les méthodes sur la pile des appels tout en déboguant
description: Découvrez comment créer une carte de code pour suivre visuellement la pile des appels pendant le débogage. En outre, découvrez que vous pouvez créer des notes sur la carte pour suivre ce que fait le code.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- call stacks, code maps
- Call Stack window, mapping calls
- debugging [Visual Studio], diagramming the call stack
- call stacks, mapping
- Call Stack window, visualizing
- debugging code visually
- debugging [Visual Studio], mapping the call stack
- call stacks, visualizing
- debugging, code maps
- Call Stack window, tracing calls visually
- Call Stack window, show on code map
- debugging [Visual Studio], tracing the call stack visually
- debugging [Visual Studio], visualizing the call stack
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 08fa0ff028140ebad421dd43fdfa53cc36b77804
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387487"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Mapper les méthodes sur la pile des appels tout en déboguant dans Visual Studio

Créez une carte de code pour effectuer un suivi visuel de la pile des appels pendant le débogage. Vous pouvez rédiger des notes sur la carte pour effectuer le suivi de ce que fait le code afin de vous concentrer sur la recherche de bogues.

 ![Débogage avec des piles d'appels sur des cartes de code](../debugger/media/debuggermap_overview.png)

 Voici ce dont vous avez besoin :

 ::: moniker range="vs-2017"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range=">=vs-2019"

- [Visual Studio Enterprise](https://visualstudio.microsoft.com/downloads)

::: moniker-end

- Code que vous pouvez déboguer, tel que Visual C#, Visual Basic, C++, JavaScript ou X + +

  Consultez l'article :

- [Vidéo : déboguer visuellement avec l’intégration du débogueur de la carte du code (Channel 9)](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012Debug-visually-with-Code-Map-debugger-integration)

- [Mapper la pile des appels](#MapStack)

- [Créer des notes sur le code](#MakeNotes)

- [Mettre à jour la carte avec la pile d’appels suivante](#UpdateMap)

- [Ajouter le code associé à la carte](#AddRelatedCode)

- [Rechercher des bogues à l’aide de la carte](#FindBugs)

- [Q & R](#QA)

  Pour plus d’informations sur les commandes et les actions que vous pouvez utiliser lorsque vous travaillez avec des cartes de code, consultez [Parcourir et réorganiser les cartes de code](../modeling/browse-and-rearrange-code-maps.md).

## <a name="map-the-call-stack"></a><a name="MapStack"></a> Mapper la pile des appels

1. Démarrez le débogage. (Clavier : **F5**)

2. Une fois que votre application passe en mode arrêt ou que vous exécutez pas à pas une fonction, choisissez **carte du code**. (Clavier : **CTRL**  +  **MAJ**  +  **`** )

     ![Choisir Carte de code pour démarrer le mappage de la pile d’appels](../debugger/media/debuggermap_choosecodemap.png)

     La pile d'appels actuelle apparaît en orange sur une nouvelle carte de code :

     ![Voir pile d'appels sur carte du code](../debugger/media/debuggermap_seeundocallstack.png)

     La carte se mettra à jour automatiquement pendant que vous continuez le débogage. Consultez [mettre à jour la carte avec la pile d’appels suivante](#UpdateMap).

## <a name="make-notes-about-the-code"></a><a name="MakeNotes"></a> Rédiger des notes sur le code

 Ajoutez des commentaires pour suivre ce qui se passe dans le code. Pour ajouter une nouvelle ligne dans un commentaire, appuyez sur **Maj + Retour**.

 ![Ajouter un commentaire à la pile d’appels sur la carte de code](../debugger/media/debuggermap_addcomment.png)

## <a name="update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a> Mettre à jour la carte avec la pile d’appels suivante

 Exécutez votre application jusqu'au point d'arrêt suivant ou exécutez pas à pas une fonction. La carte ajoute une nouvelle pile d'appels.

 ![Mettre à jour le Code de mappage avec la pile d'appels suivante](../debugger/media/debuggermap_addclearcallstack.png)

## <a name="add-related-code-to-the-map"></a><a name="AddRelatedCode"></a> Ajouter du code associé à la carte

 Vous disposez maintenant d’une carte : qu’en est-il de la suite ? Si vous utilisez C# ou Visual Basic, ajoutez des éléments, tels que des champs, des propriétés et d’autres méthodes, pour suivre ce qui se passe dans le code.

 Double-cliquez sur une méthode pour afficher sa définition de code ou utilisez le menu contextuel pour la méthode. (Clavier : sélectionnez la méthode sur la carte et appuyez sur **F12**)

 ![Aller à la définition du code pour une méthode sur une carte du code](../debugger/media/debuggermap_gotocodedefinition.png)

 Ajoutez les éléments que vous souhaitez suivre sur la carte.

 ![Afficher les champs dans une méthode sur la carte de code de la pile d’appels](../debugger/media/debuggermap_showfields.png)

> [!NOTE]
> Par défaut, l'ajout d'éléments à la carte ajoute également les nœuds des groupes parents, comme la classe, l'espace de noms et l'assembly. Bien que cela soit utile, vous pouvez conserver la carte simple en désactivant cette fonctionnalité à l’aide du bouton **inclure les parents** dans la barre d’outils de la carte, ou en appuyant sur **CTRL** lorsque vous ajoutez des éléments.

 ![Champs associés à une méthode sur la carte du code de la pile d’appels](../debugger/media/debuggermap_showedfields.png)

 Vous pouvez ici voir aisément quelles méthodes utilisent les mêmes champs. Les derniers éléments ajoutés apparaissent en vert.

 Poursuivez l'élaboration de la carte pour afficher davantage de code.

 ![Voir les méthodes qui utilisent un champ : carte du code de la pile des appels](../debugger/media/debuggermap_findallreferences.png)

 ![Méthodes qui utilisent un champ sur la carte du code de la pile d’appels](../debugger/media/debuggermap_foundallreferences.png)

## <a name="find-bugs-using-the-map"></a><a name="FindBugs"></a> Rechercher des bogues à l’aide de la carte

 La visualisation de votre code peut vous aider à rechercher des bogues plus rapidement. Par exemple, supposons que vous recherchez un bogue dans un programme de dessin. Lorsque vous tracez une ligne et essayez de l'annuler, rien ne se produit jusqu'à ce que vous traciez une autre ligne.

 Vous définissez donc des points d'arrêt dans les méthodes `clear`, `undo` et `Repaint`, vous démarrez le débogage et vous générez une carte comme celle-ci :

 ![Ajouter une autre pile d'appels au code de mappage](../debugger/media/debuggermap_addpaintobjectcallstack.png)

 Vous constatez que tous les mouvements de l'utilisateur sur la carte appellent `Repaint`, à l'exception de `undo`. Cela peut expliquer pourquoi `undo` ne fonctionne pas immédiatement.

 Après avoir corrigé le bogue et poursuivi l'exécution du programme, la carte ajoute le nouvel appel de `undo` à `Repaint` :

 ![Ajouter un nouvel appel de méthode à la pile d'appels sur le code de mappage](../debugger/media/debuggermap_addnewcallforrepaint.png)

## <a name="q--a"></a><a name="QA"></a> Q & A

- **Tous les appels n’apparaissent pas sur la carte. Pourquoi?**

   Par défaut, seul votre propre code apparaît sur la carte. Pour afficher le code externe, activez-le dans la fenêtre **pile des appels** :

   ![Afficher du code externe à l'aide de la fenêtre Pile des appels](../debugger/media/debuggermap_callstackmenu.png)

   ou désactivez **activer uniquement mon code** dans les options de débogage de Visual Studio :

   ![Afficher du code externe à l'aide de la boîte de dialogue Options](../debugger/media/debuggermap_debugoptions.png)

- **La modification de la carte affecte-t-elle le code ?**

   La modification de la carte n’affecte en rien le code. N'hésitez pas à renommer, déplacer ou supprimer tout élément de la carte.

- **Signification de ce message : « le diagramme peut être basé sur une version antérieure du code » ?**

   Il se peut que le code ait changé après la dernière mise à jour de la carte. Par exemple, un appel sur la carte peut ne plus exister dans le code. Fermez le message et essayez de régénérer la solution avant de remettre à jour la carte.

- **Comment faire contrôler la disposition de la carte ?**

   Ouvrez le menu **disposition** dans la barre d’outils de la carte :

  - Modifiez la disposition par défaut.

  - Pour arrêter la réorganisation automatique de la carte, désactivez la **mise en forme automatique lors du débogage**.

  - Pour réorganiser le mappage le moins possible lorsque vous ajoutez des éléments, désactivez la **disposition incrémentielle**.

- **Puis-je partager la carte avec d'autres ?**

   Vous pouvez exporter la carte, l’envoyer à d’autres personnes si vous disposez de Microsoft Outlook ou l’enregistrer dans votre solution afin de pouvoir l’archiver dans le contrôle de code source.

   ![Partager la carte du code de la pile d’appels avec les autres](../debugger/media/debuggermap_sharewithothers.png)

- **Comment puis-je arrêter l'ajout automatique de nouvelles piles d'appels par la carte ?**

   Cliquez ![ sur le bouton &#45; afficher automatiquement la pile des appels sur ](../debugger/media/debuggermap_automaticupdateicon.gif) la carte du code dans la barre d’outils de la carte. Pour ajouter manuellement la pile d’appels actuelle à la carte, appuyez sur **CTRL**  +  **MAJ**  +  **`** .

   La carte continuera de mettre en surbrillance les piles d’appels existantes sur la carte pendant le débogage.

- **Que signifient les flèches et les icônes d'élément ?**

   Pour obtenir plus d’informations sur un élément, placez le pointeur de la souris sur celui-ci et regardez l’info-bulle de l’élément. Vous pouvez également examiner la **légende** pour savoir ce que signifie chaque icône.

   ![Que signifient les icônes sur la carte du code de la pile d'appels ?](../debugger/media/debuggermap_showlegend.png)

  Consultez l'article :

- [Mapper la pile des appels](#MapStack)

- [Créer des notes sur le code](#MakeNotes)

- [Mettre à jour la carte avec la pile d’appels suivante](#UpdateMap)

- [Ajouter le code associé à la carte](#AddRelatedCode)

- [Rechercher des bogues à l’aide de la carte](#FindBugs)

## <a name="see-also"></a>Voir aussi

- [Mapper les dépendances à travers vos solutions](../modeling/map-dependencies-across-your-solutions.md)
- [Utiliser des cartes du code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)
- [Rechercher des problèmes potentiels à l’aide des analyseurs de carte du code](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Parcourir et réorganiser des cartes de code](../modeling/browse-and-rearrange-code-maps.md)
