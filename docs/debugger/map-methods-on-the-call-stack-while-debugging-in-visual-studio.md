---
title: Créer une carte visuelle de la pile des appels | Microsoft Docs
ms.date: 11/26/2018
ms.topic: conceptual
f1_keywords:
- vs.progression.debugwithcodemaps
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 118b8a6c8d857e626d39cf27d2767f75cd0550ee
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704811"
---
# <a name="create-a-visual-map-of-the-call-stack-while-debugging-c-visual-basic-c-javascript"></a>Créer une carte visuelle de la pile des appels pendant le débogage (C#, Visual Basic, C++, JavaScript)

Créez une carte de code pour effectuer un suivi visuel de la pile des appels pendant le débogage. Vous pouvez rédiger des notes sur la carte pour effectuer le suivi de ce que fait le code afin de vous concentrer sur la recherche de bogues.

Pour une procédure pas à pas, regardez cette vidéo : [Vidéo : Déboguez visuellement avec intégration du débogueur (Channel 9)](http://go.microsoft.com/fwlink/?LinkId=293418)

Pour plus d’informations des commandes et des actions que vous pouvez utiliser des cartes de code, consultez [Parcourir et réorganiser des cartes de code](../modeling/browse-and-rearrange-code-maps.md).

>[!IMPORTANT]
>Vous pouvez créer uniquement dans les cartes de code [Visual Studio Enterprise edition](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017).

Voici un rapide coup de œil à une carte de code :

 ![Débogage avec les piles d’appels sur les cartes de code](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")

##  <a name="MapStack"></a> Mapper la pile des appels

1. Dans Visual Studio Enterprise C#, Visual Basic, C++ ou JavaScript du projet, démarrez le débogage en sélectionnant **déboguer** > **démarrer le débogage** ou en appuyant sur **F5**.

1. Une fois votre application passe en mode arrêt ou que vous parcourez une fonction, sélectionnez **déboguer** > **carte de Code**, ou appuyez sur **Ctrl**+**MAJ** +**`**.

   La pile d'appels actuelle apparaît en orange sur une nouvelle carte de code :

   ![Voir pile des appels sur carte de code](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")

Le code mappe automatiquement les mises à jour durant le débogage. Modification des éléments de la carte ou la disposition n’affecte pas le code en aucune façon. N'hésitez pas à renommer, déplacer ou supprimer tout élément de la carte.

Pour obtenir plus d’informations sur un élément, pointez dessus et consultez l’info-bulle. Vous pouvez également sélectionner **légende** dans la barre d’outils pour savoir ce que signifie chaque icône.

![Légende de la carte de code](../debugger/media/debuggermap_showlegend.png "légende de la carte de Code")

>[!NOTE]
>Le message **le diagramme peut être basé sur une version antérieure du code** en haut du code de mappage signifie que le code peut ont changé après la dernière mise à jour de la carte. Par exemple, un appel sur la carte peut ne plus exister dans le code. Fermez le message et essayez de régénérer la solution avant de remettre à jour la carte.

## <a name="map-external-code"></a>Code externe de la carte

Par défaut, seul votre propre code apparaît sur la carte. Pour afficher le code externe sur la carte :

- Avec le bouton droit dans le **pile des appels** fenêtre et sélectionnez **afficher le Code externe**:

  ![Afficher le code externe à l’aide de la fenêtre Pile des appels](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")
- Ou, désélectionnez **activer uniquement mon Code** dans Visual Studio **outils** (ou **déboguer**) > **Options**  >   **Débogage**:

  ![Afficher le code externe à l’aide de la boîte de dialogue Options](../debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")

## <a name="control-the-maps-layout"></a>Contrôler la disposition de la carte

Modifier la disposition de la carte n’affecte pas le code en aucune façon.

Pour contrôler la disposition de la carte, sélectionnez le **disposition** menu sur la barre d’outils de la carte.

Dans le **disposition** menu, vous pouvez :

-   Modifiez la disposition par défaut.
-   Arrêter la réorganisation automatique, de la carte en désélectionnant **disposer automatiquement lors du débogage**.
-   Réorganiser la carte le moins possible lorsque vous ajoutez des éléments, désélectionnez l’option **disposition incrémentielle**.

##  <a name="MakeNotes"></a> Rédiger des notes sur le code

Vous pouvez ajouter des commentaires pour effectuer le suivi de ce qui se passe dans le code.

Pour ajouter un commentaire, avec le bouton droit dans la carte de code et sélectionnez **modifier** > **nouveau commentaire**, puis tapez le commentaire.

Pour ajouter une nouvelle ligne dans un commentaire, appuyez sur **MAJ**+**entrée**.

 ![Ajouter un commentaire à la pile des appels sur carte de code](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")

##  <a name="UpdateMap"></a> Mettre à jour la carte avec la pile d’appels suivante

Lorsque vous exécutez votre application pour le point d’arrêt suivant ou l’étape dans une fonction, la carte ajoute automatiquement les nouvelles piles d’appels.

![Carte de code de mise à jour avec la pile d’appels suivante](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")

Pour arrêter le mappage de l’ajout de nouvelles piles d’appels automatiquement, sélectionnez ![pile des appels de l’afficher sur la carte de code automatiquement](../debugger/media/debuggermap_automaticupdateicon.gif "pile des appels de l’afficher sur la carte de code automatiquement") sur la barre d’outils de carte de code. La carte continue à mettre en surbrillance les piles d’appels existantes. Pour ajouter manuellement la pile des appels actuelle à la carte, appuyez sur **Ctrl**+**MAJ**+**`**.

##  <a name="AddRelatedCode"></a> Ajouter du code associé à la carte

Maintenant que vous avez un mappage, en C# ou Visual Basic, vous pouvez ajouter des éléments tels que des champs, propriétés et d’autres méthodes, pour effectuer le suivi de ce qui se passe dans le code.

Pour passer à la définition d’une méthode dans le code, double-cliquez sur la méthode dans le mappage, ou sélectionnez-le et appuyez sur **F12**, ou faites un clic droit et sélectionnez **atteindre la définition**.

![Atteindre la définition de code pour une méthode sur la carte de code](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")

Pour ajouter des éléments que vous souhaitez effectuer le suivi à la carte, une méthode d’avec le bouton droit et sélectionnez les éléments que vous souhaitez effectuer le suivi. Les derniers éléments ajoutés apparaissent en vert.

![Champs associés à une méthode sur la carte de code de pile des appels](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")

>[!NOTE]
>Par défaut, l'ajout d'éléments à la carte ajoute également les nœuds des groupes parents, comme la classe, l'espace de noms et l'assembly. Vous pouvez activer cette fonctionnalité et en sélectionnant le **inclure les Parents** bouton sur la barre d’outils de carte de code, ou en appuyant sur **Ctrl** pendant que vous ajoutez des éléments.

![Afficher les champs dans une méthode sur la carte de code de pile des appels](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")

Poursuivez l'élaboration de la carte pour afficher davantage de code.

 ![Consultez les méthodes qui utilisent un champ : carte code pile d’appels](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")

 ![Les méthodes qui utilisent un champ sur la carte de code de pile des appels](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")

##  <a name="FindBugs"></a> Rechercher des bogues à l’aide de la carte
 La visualisation de votre code peut vous aider à rechercher des bogues plus rapidement. Par exemple, supposons que vous recherchiez un bogue dans une application de dessin. Lorsque vous tracez une ligne et essayez de l'annuler, rien ne se produit jusqu'à ce que vous traciez une autre ligne.

 Vous définissez donc des points d'arrêt dans les méthodes `clear`, `undo` et `Repaint`, vous démarrez le débogage et vous générez une carte comme celle-ci :

 ![Ajouter une autre pile des appels à la carte de code](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")

 Vous constatez que tous les mouvements de l'utilisateur sur la carte appellent `Repaint`, à l'exception de `undo`. Cela peut expliquer pourquoi `undo` ne fonctionne pas immédiatement.

 Une fois que vous corrigez le bogue et continuez à exécuter l’application, la carte ajoute le nouvel appel de `undo` à `Repaint`:

 ![Ajouter la nouvelle pile d’appel à l’autre méthode sur la carte de code](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")

## <a name="share-the-map-with-others"></a>Partager la carte avec d’autres utilisateurs

Vous pouvez exporter un mappage, envoyer à d’autres personnes avec Microsoft Outlook, enregistrez-le dans votre solution et archivez-le dans le contrôle de version.

Pour partager ou enregistrer la carte, utilisez **partager** dans la barre d’outils de carte de code.

![Carte code pile d’appels partage avec d’autres utilisateurs](../debugger/media/debuggermap_sharewithothers.png "carte code pile d’appels partage avec d’autres utilisateurs")

## <a name="see-also"></a>Voir aussi
[Mapper les dépendances à travers vos solutions](../modeling/map-dependencies-across-your-solutions.md)

[Utiliser des cartes de code pour déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)

[Rechercher des problèmes potentiels à l’aide des analyseurs de carte du code](../modeling/find-potential-problems-using-code-map-analyzers.md)

[Parcourir et réorganiser des cartes de code](../modeling/browse-and-rearrange-code-maps.md)
