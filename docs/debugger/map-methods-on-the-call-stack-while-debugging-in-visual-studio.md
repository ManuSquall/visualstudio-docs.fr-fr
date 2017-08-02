---
title: "Mapper les méthodes sur la pile des appels lors du débogage dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: get-started-article
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
caps.latest.revision: 39
author: mikejo5000
ms.author: mikejo
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ab08446140608a65b6894b3015c52227040611fd
ms.lasthandoff: 02/22/2017

---
# <a name="map-methods-on-the-call-stack-while-debugging-in-visual-studio"></a>Mapper les méthodes sur la pile des appels tout en déboguant dans Visual Studio
Créez une carte de code pour effectuer un suivi visuel de la pile des appels pendant le débogage. Vous pouvez rédiger des notes sur la carte pour effectuer le suivi de ce que fait le code afin de vous concentrer sur la recherche de bogues.  
  
 ![Débogage avec les piles d’appels sur les cartes de code](../debugger/media/debuggermap_overview.png "DebuggerMap_Overview")  
  
 Vous aurez besoin de :  
  
-   [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)  
  
-   De code que vous pouvez déboguer, comme Visual C# .NET, Visual Basic .NET, C++, JavaScript ou X++  
  
 Voir : [vidéo : déboguer visuellement avec intégration du débogueur de Code de mappage (Channel 9)](http://go.microsoft.com/fwlink/?LinkId=293418) • [mapper la pile des appels](#MapStack) • [rédiger des notes sur le code](#MakeNotes) • [mise à jour de la carte avec la pile d’appels suivante](#UpdateMap) • [ajouter du code associé à la carte](#AddRelatedCode) • [recherche des bogues à l’aide de la carte](#FindBugs) • [Q & A](#QA)  
  
 Pour plus d’informations sur les commandes et les actions que vous pouvez utiliser lors de l’utilisation des cartes de code, consultez [Parcourir et réorganiser des cartes de code](../modeling/browse-and-rearrange-code-maps.md).  
  
##  <a name="a-namemapstacka-map-the-call-stack"></a><a name="MapStack"></a>Mapper la pile des appels  
  
1.  Démarrez le débogage. (Clavier : **F5**)  
  
2.  Une fois que votre application passe en mode arrêt ou que vous parcourez une fonction, choisissez **Code de mappage**. (Keyboard: **Ctrl** + **Shift** + **`**)  
  
     ![Choisir carte du Code pour démarrer la pile des appels de mappage](~/debugger/media/debuggermap_choosecodemap.png "DebuggerMap_ChooseCodeMap")  
  
     La pile d’appels actuelle apparaît en orange sur une nouvelle carte de code :  
  
     ![Voir pile des appels sur carte du code](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap_SeeUndoCallStack")  
  
     La carte se mettra à jour automatiquement pendant que vous continuez le débogage. Consultez la page [mise à jour de la carte avec la pile d’appels suivante](#UpdateMap).  
  
##  <a name="a-namemakenotesa-make-notes-about-the-code"></a><a name="MakeNotes"></a>Rédiger des notes à propos du code  
 Ajoutez des commentaires pour effectuer le suivi de ce qui se passe dans le code. Pour ajouter une nouvelle ligne dans un commentaire, appuyez sur **MAJ + retour**.  
  
 ![Ajouter un commentaire à la pile des appels sur carte du code](../debugger/media/debuggermap_addcomment.png "DebuggerMap_AddComment")  
  
##  <a name="a-nameupdatemapa-update-the-map-with-the-next-call-stack"></a><a name="UpdateMap"></a>Mise à jour de la carte avec la pile d’appels suivante  
 Exécutez votre application jusqu'au point d'arrêt suivant ou exécutez pas à pas une fonction. La carte ajoute une nouvelle pile d'appels.  
  
 ![Carte de code de mise à jour avec la pile d’appels suivante](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap_AddClearCallStack")  
  
##  <a name="a-nameaddrelatedcodea-add-related-code-to-the-map"></a><a name="AddRelatedCode"></a>Ajouter du code associé à la carte  
 Vous disposez désormais d'une carte, mais comment continuer ? Si vous utilisez Visual C# .NET ou Visual Basic .NET, ajoutez des éléments, tels que des champs, des propriétés et d'autres méthodes, pour suivre ce qui se passe dans le code.  
  
 Double-cliquez sur une méthode pour afficher sa définition de code ou utilisez le menu contextuel pour la méthode. (Clavier : sélectionnez la méthode sur la carte et appuyez sur **F12**)  
  
 ![Atteindre la définition du code pour une méthode sur la carte de code](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap_GoToCodeDefinition")  
  
 Ajoutez les éléments que vous souhaitez suivre sur la carte.  
  
 ![Afficher les champs dans une méthode sur la carte de code de pile des appels](../debugger/media/debuggermap_showfields.png "DebuggerMap_ShowFields")  
  
> [!NOTE]
>  Par défaut, l'ajout d'éléments à la carte ajoute également les nœuds des groupes parents, comme la classe, l'espace de noms et l'assembly. Bien que cela soit utile, vous pouvez conserver le mappage simple en désactivant cette fonctionnalité à l’aide de la **inclure les Parents** bouton sur la barre d’outils de mappage, ou en appuyant sur **CTRL** lorsque vous ajoutez des éléments.  
  
 ![Champs associés à une méthode sur la carte de code de pile des appels](../debugger/media/debuggermap_showedfields.png "DebuggerMap_ShowedFields")  
  
 Vous pouvez ici voir aisément quelles méthodes utilisent les mêmes champs. Les derniers éléments ajoutés apparaissent en vert.  
  
 Poursuivez l'élaboration de la carte pour afficher davantage de code.  
  
 ![Consultez les méthodes qui utilisent un champ : carte du code pile des appels](../debugger/media/debuggermap_findallreferences.png "DebuggerMap_FindAllReferences")  
  
 ![Les méthodes qui utilisent un champ sur la carte de code de pile des appels](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap_FoundAllReferences")  
  
##  <a name="a-namefindbugsa-find-bugs-using-the-map"></a><a name="FindBugs"></a>Rechercher des bogues à l’aide de la carte  
 La visualisation de votre code peut vous aider à rechercher des bogues plus rapidement. Par exemple, supposons que vous recherchiez un bogue dans un programme de dessin. Lorsque vous tracez une ligne et essayez de l'annuler, rien ne se produit jusqu'à ce que vous traciez une autre ligne.  
  
 Vous définissez donc des points d'arrêt dans les méthodes `clear`, `undo` et `Repaint`, vous démarrez le débogage et vous générez une carte comme celle-ci :  
  
 ![Ajouter une autre pile des appels au code de mappage](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap_AddPaintObjectCallStack")  
  
 Vous constatez que tous les mouvements de l'utilisateur sur la carte appellent `Repaint`, à l'exception de `undo`. Cela peut expliquer pourquoi `undo` ne fonctionne pas immédiatement.  
  
 Après avoir corrigé le bogue et poursuivi l'exécution du programme, la carte ajoute le nouvel appel de `undo` à `Repaint` :  
  
 ![Ajouter la nouvelle pile d’appel à l’autre méthode sur carte du code](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap_AddNewCallForRepaint")  
  
##  <a name="a-nameqaa-q--a"></a><a name="QA"></a> Q et R  
  
-   **Pas tous les appels apparaissent sur la carte. Pourquoi ?**  
  
     Par défaut, seul votre propre code apparaît sur la carte. Pour afficher le code externe, activez-le dans la **pile des appels** fenêtre :  
  
     ![Afficher le code externe à l’aide de la fenêtre Pile des appels](~/debugger/media/debuggermap_callstackmenu.png "DebuggerMap_CallStackMenu")  
  
     ou désactiver **activer uniquement mon Code** dans les options de débogage Visual Studio :  
  
     ![Afficher le code externe à l’aide de la boîte de dialogue Options](~/debugger/media/debuggermap_debugoptions.png "DebuggerMap_DebugOptions")  
  
-   **Modification de la carte affecte-t-elle le code ?**  
  
     La modification de la carte n'affecte en aucune manière le code. N'hésitez pas à renommer, déplacer ou supprimer tout élément de la carte.  
  
-   **Ce que signifie le message : « le diagramme peut être basé sur une version antérieure du code » ?**  
  
     Il se peut que le code ait changé après la dernière mise à jour de la carte. Par exemple, un appel sur la carte peut ne plus exister dans le code. Fermez le message et essayez de régénérer la solution avant de remettre à jour la carte.  
  
-   **Comment contrôler la disposition de la carte ?**  
  
     Ouvrez la **disposition** menu sur la barre d’outils de la carte :  
  
    -   Modifiez la disposition par défaut.  
  
    -   Pour arrêter la réorganisation automatique de la carte, désactivez **disposer automatiquement lors du débogage**.  
  
    -   Pour réorganiser la carte aussi peu que possible lorsque vous ajoutez des éléments, désactivez **disposition incrémentielle**.  
  
-   **Puis-je partager la carte avec d’autres personnes ?**  
  
     Vous pouvez exporter la carte, l’envoyer à d’autres personnes si vous disposez de Microsoft Outlook ou l’enregistrer dans votre solution afin de pouvoir la vérifier dans Team Foundation Version Control.  
  
     ![Carte du code pile d’appels partage avec d’autres](../debugger/media/debuggermap_sharewithothers.png "DebuggerMap_ShareWithOthers")  
  
-   **Comment arrêter l’ajout automatique de nouvelles piles d’appels par la carte ?**  
  
     Choisissez ![bouton - Afficher la pile des appels sur le code de mappage automatiquement](~/debugger/media/debuggermap_automaticupdateicon.gif "DebuggerMap_AutomaticUpdateIcon") sur la barre d’outils de la carte. Pour ajouter manuellement la pile des appels en cours à la carte, appuyez sur **Ctrl** + **MAJ** + **`**.  
  
     La carte continuera de mettre en surbrillance les piles d'appels existantes sur la carte pendant le débogage.  
  
-   **Les flèches et les icônes de signification**  
  
     Pour obtenir plus d'informations sur un élément, placez le pointeur de la souris sur celui-ci et consultez l'info-bulle. Vous pouvez également consulter le **légende** pour découvrir la signification de chaque icône.  
  
     ![Que signifient les icônes sur la carte de code de pile des appels ? ] (../debugger/media/debuggermap_showlegend.png "DebuggerMap_ShowLegend")  
  
 Voir : [mapper la pile des appels](#MapStack) • [rédiger des notes sur le code](#MakeNotes) • [mise à jour de la carte avec la pile d’appels suivante](#UpdateMap) • [ajouter du code associé à la carte](#AddRelatedCode) • [rechercher des bogues à l’aide de la carte](#FindBugs)  
  
## <a name="see-also"></a>Voir aussi  
 [Mapper les dépendances dans vos solutions](../modeling/map-dependencies-across-your-solutions.md)   
 [Utilisez des cartes de code à déboguer vos applications](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Rechercher des problèmes potentiels à l’aide des analyseurs de carte de code](../modeling/find-potential-problems-using-code-map-analyzers.md)   
 [Parcourir et réorganiser des cartes de code](../modeling/browse-and-rearrange-code-maps.md)
