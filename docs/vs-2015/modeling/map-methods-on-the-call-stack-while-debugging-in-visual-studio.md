---
title: Mapper les méthodes sur la pile des appels tout en déboguant
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
caps.latest.revision: 43
author: MikeJo5000
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2a2c6e95822794394dbdfc7f53104b31b7c17ea9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296078"
---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Mapper les méthodes sur la pile des appels tout en déboguant dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Créez une carte de code pour effectuer un suivi visuel de la pile des appels pendant le débogage. Vous pouvez rédiger des notes sur la carte pour effectuer le suivi de ce que fait le code afin de vous concentrer sur la recherche de bogues.

 ![Débogage avec des piles d’appels sur des cartes de code](../debugger/media/debuggermap-overview.png "DebuggerMap_Overview")

 Vous aurez besoin de :

- [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)

- De code que vous pouvez déboguer, comme Visual C# .NET, Visual Basic .NET, C++, JavaScript ou X++

  Voir : [vidéo : déboguer visuellement à l’aide de l’intégration du débogueur de la carte du code (Channel 9)](https://go.microsoft.com/fwlink/?LinkId=293418) • [mapper la pile des appels](#MapStack) • [faire des notes sur le code](#MakeNotes) • [mettre à jour la carte avec la pile d’appels suivante](#UpdateMap) • [Ajouter le code associé à la carte](#AddRelatedCode) • [Rechercher des bogues à l’aide de la carte](#FindBugs) • [Q & A](#QA)

  Pour plus de détails sur les commandes et les actions que vous pouvez utiliser quand vous travaillez avec des cartes de code, consultez [Parcourir et réorganiser des cartes de code](../modeling/browse-and-rearrange-code-maps.md).

## <a name="MapStack"></a> Mapper la pile des appels

1. Démarrez le débogage. (Clavier : **F5**)

2. Une fois que votre application passe en mode arrêt ou que vous parcourez une fonction, choisissez **carte de Code**. (Clavier : **Ctrl** + **MAJ** +  **`** )

     ![Choisir une carte de code pour démarrer le mappage de la pile des appels](../debugger/media/debuggermap-choosecodemap.png "DebuggerMap_ChooseCodeMap")

     La pile d'appels actuelle apparaît en orange sur une nouvelle carte de code :

     ![Voir pile des appels sur la carte du code](../debugger/media/debuggermap-seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

     La carte se mettra à jour automatiquement pendant que vous continuez le débogage. Consultez [Mettre à jour la carte avec la pile d'appels suivante](#UpdateMap).

## <a name="MakeNotes"></a> Rédiger des notes sur le code
 Ajoutez des commentaires pour effectuer le suivi de ce qui se passe dans le code. Pour ajouter une nouvelle ligne dans des commentaires, appuyez sur **Maj + Entrée**.

 ![Ajouter un commentaire à la pile d’appels sur la carte du code](../debugger/media/debuggermap-addcomment.png "DebuggerMap_AddComment")

## <a name="UpdateMap"></a> Mettre à jour la carte avec la pile d’appels suivante
 Exécutez votre application jusqu'au point d'arrêt suivant ou exécutez pas à pas une fonction. La carte ajoute une nouvelle pile d'appels.

 ![Mettre à jour la carte de code avec la pile des appels suivante](../debugger/media/debuggermap-addclearcallstack.png "DebuggerMap_AddClearCallStack")

## <a name="AddRelatedCode"></a> Ajouter du code associé à la carte
 Vous disposez désormais d'une carte, mais comment continuer ? Si vous utilisez Visual C# .NET ou Visual Basic .NET, ajoutez des éléments, tels que des champs, des propriétés et d'autres méthodes, pour suivre ce qui se passe dans le code.

 Double-cliquez sur une méthode pour afficher sa définition de code ou utilisez le menu contextuel pour la méthode. (Clavier : sélectionnez la méthode sur la carte et appuyez sur **F12**)

 ![Atteindre la définition de code pour une méthode sur la carte du code](../debugger/media/debuggermap-gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

 Ajoutez les éléments que vous souhaitez suivre sur la carte.

 ![Afficher les champs dans une méthode sur la carte du code de la pile des appels](../debugger/media/debuggermap-showfields.png "DebuggerMap_ShowFields")

> [!NOTE]
> Par défaut, l'ajout d'éléments à la carte ajoute également les nœuds des groupes parents, comme la classe, l'espace de noms et l'assembly. Bien que ceci soit utile, vous pouvez conserver la carte simple en désactivant cette fonctionnalité à l'aide du bouton **Inclure les parents** sur la barre d'outils de la carte, ou en appuyant sur **Ctrl** quand vous ajoutez des éléments.

 ![Champs associés à une méthode sur la carte du code de la pile des appels](../debugger/media/debuggermap-showedfields.png "DebuggerMap_ShowedFields")

 Vous pouvez ici voir aisément quelles méthodes utilisent les mêmes champs. Les derniers éléments ajoutés apparaissent en vert.

 Poursuivez l'élaboration de la carte pour afficher davantage de code.

 ![Consultez les méthodes qui utilisent un champ : carte du code de la pile des appels](../debugger/media/debuggermap-findallreferences.png "DebuggerMap_FindAllReferences")

 ![Méthodes qui utilisent un champ sur la carte du code de la pile des appels](../debugger/media/debuggermap-foundallreferences.png "DebuggerMap_FoundAllReferences")

## <a name="FindBugs"></a> Rechercher des bogues à l’aide de la carte
 La visualisation de votre code peut vous aider à rechercher des bogues plus rapidement. Par exemple, supposons que vous recherchiez un bogue dans un programme de dessin. Lorsque vous tracez une ligne et essayez de l'annuler, rien ne se produit jusqu'à ce que vous traciez une autre ligne.

 Vous définissez donc des points d'arrêt dans les méthodes `clear`, `undo` et `Repaint`, vous démarrez le débogage et vous générez une carte comme celle-ci :

 ![Ajouter une autre pile d’appels à la carte de code](../debugger/media/debuggermap-addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Vous constatez que tous les mouvements de l'utilisateur sur la carte appellent `Repaint`, à l'exception de `undo`. Cela peut expliquer pourquoi `undo` ne fonctionne pas immédiatement.

 Après avoir corrigé le bogue et poursuivi l'exécution du programme, la carte ajoute le nouvel appel de `undo` à `Repaint` :

 ![Ajouter un nouvel appel de méthode à la pile d’appels sur la carte de code](../debugger/media/debuggermap-addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="QA"></a> Q et R

- **Tous les appels n’apparaissent pas sur la carte. Pourquoi?**

   Par défaut, seul votre propre code apparaît sur la carte. Pour afficher le code externe, activez-le dans la fenêtre **Pile des appels** :

   ![Afficher le code externe à l’aide de la fenêtre pile des appels](../debugger/media/debuggermap-callstackmenu.png "DebuggerMap_CallStackMenu")

   ou désactivez **Activer Uniquement mon Code** dans les options de débogage de Visual Studio :

   ![Afficher le code externe à l’aide de la boîte de dialogue Options](../debugger/media/debuggermap-debugoptions.png "DebuggerMap_DebugOptions")

- **Modification de la carte affecte-t-elle le code ?**

   La modification de la carte n'affecte en aucune manière le code. N'hésitez pas à renommer, déplacer ou supprimer tout élément de la carte.

- **Signification de ce message : « le diagramme peut être basé sur une version antérieure du code » ?**

   Il se peut que le code ait changé après la dernière mise à jour de la carte. Par exemple, un appel sur la carte peut ne plus exister dans le code. Fermez le message et essayez de régénérer la solution avant de remettre à jour la carte.

- **Comment faire contrôler la disposition de la carte ?**

   Ouvrez le **disposition** menu sur la barre d’outils de mappage :

  - Modifiez la disposition par défaut.

  - Pour arrêter la réorganisation automatique de la carte, désactivez **Disposer automatiquement lors du débogage**.

  - Pour réorganiser la carte le moins possible lorsque vous ajoutez des éléments, désactivez **Disposition incrémentielle**.

- **Puis-je partager la carte avec d’autres personnes ?**

   Vous pouvez exporter la carte, l’envoyer à d’autres personnes si vous disposez de Microsoft Outlook ou l’enregistrer dans votre solution afin de pouvoir la vérifier dans Team Foundation Version Control.

   ![Partager la carte de code de la pile des appels avec d’autres utilisateurs](../debugger/media/debuggermap-sharewithothers.png "DebuggerMap_ShareWithOthers")

- **Comment empêcher le mappage de l’ajout de nouvelles piles d’appels automatiquement ?**

   Choisissez ![bouton &#45; pile des appels de l’afficher sur la carte de code automatiquement](../debugger/media/debuggermap-automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") sur la barre d’outils de la carte. Pour ajouter manuellement la pile des appels actuelle à la carte, appuyez sur **Ctrl** + **MAJ** +  **`** .

   La carte continuera de mettre en surbrillance les piles d'appels existantes sur la carte pendant le débogage.

- **Que les icônes de l’élément et les flèches signifient ?**

   Pour obtenir plus d'informations sur un élément, placez le pointeur de la souris sur celui-ci et consultez l'info-bulle. Vous pouvez également examiner la **Légende** pour découvrir la signification de chaque icône.

   ![Que signifient les icônes sur la carte du code de la pile d’appels ?](../debugger/media/debuggermap-showlegend.png "DebuggerMap_ShowLegend")

  Voir : [Mapper la pile des appels](#MapStack) • [Rédiger des notes sur le code](#MakeNotes) • [Mettre à jour la carte avec la pile d'appels suivante](#UpdateMap) • [Ajouter du code associé à la carte](#AddRelatedCode) • [Rechercher des bogues à l'aide de la carte](#FindBugs)

## <a name="see-also"></a>Voir aussi
 [Mapper les dépendances dans vos solutions](../modeling/map-dependencies-across-your-solutions.md) [utiliser des cartes de code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md) [Rechercher des problèmes potentiels à l’aide d’analyseurs de carte de code](../modeling/find-potential-problems-using-code-map-analyzers.md) [Parcourir et réorganiser les cartes de code](../modeling/browse-and-rearrange-code-maps.md)
