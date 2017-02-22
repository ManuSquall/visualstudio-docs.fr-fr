---
title: "Mapper les m&#233;thodes sur la pile des appels tout en d&#233;boguant dans Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "vs.progression.debugwithcodemaps"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Fenêtre Pile des appels, appels de mappage"
  - "Fenêtre Pile des appels, afficher sur le plan de code"
  - "Fenêtre Pile des appels, tracer visuellement les appels"
  - "Fenêtre Pile des appels, visualiser"
  - "piles d'appels, plans de code"
  - "piles d'appels, mapper"
  - "piles d'appels, visualiser"
  - "déboguer (Visual Studio), créer un schéma de la pile des appels"
  - "déboguer (Visual Studio), mapper la pile des appels"
  - "déboguer (Visual Studio), tracer la pile des appels visuellement"
  - "déboguer (Visual Studio), visualiser la pile des appels"
  - "débogage visuel de code"
  - "débogage, plans de code"
ms.assetid: d6a72e5e-f88d-46fc-94a3-1789d34805ef
caps.latest.revision: 39
author: "mikejo5000"
ms.author: "mikejo"
manager: "douge"
caps.handback.revision: 39
---
# Mapper les m&#233;thodes sur la pile des appels tout en d&#233;boguant dans Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Créez une carte de code pour effectuer un suivi visuel de la pile des appels pendant le débogage.  Vous pouvez rédiger des notes sur la carte pour effectuer le suivi de ce que fait le code afin de vous concentrer sur la recherche de bogues.  
  
 ![Débogage avec des piles d'appels sur des cartes de code](../debugger/media/debuggermap_overview.png "DebuggerMap\_Overview")  
  
 Vous aurez besoin de :  
  
-   [Visual Studio Enterprise](https://www.visualstudio.com/downloads/download-visual-studio-vs)  
  
-   De code que vous pouvez déboguer, comme Visual C\# .NET, Visual Basic .NET, C\+\+, JavaScript ou X\+\+  
  
 Consultez : [Vidéo : déboguer visuellement avec l'intégration du débogueur de la carte de code \(Channel 9\)](http://go.microsoft.com/fwlink/?LinkId=293418) •[Mapper la pile des appels](#MapStack) • [Rédiger des notes sur le code](#MakeNotes) • [Mettre à jour la carte avec la pile d'appels suivante](#UpdateMap) • [Ajouter du code associé à la carte](#AddRelatedCode) • [Rechercher des bogues à l'aide de la carte](#FindBugs) • [Q et R](#QA)  
  
 Pour plus de détails sur les commandes et les actions que vous pouvez utiliser quand vous travaillez avec des cartes de code, consultez [Browse and rearrange code maps](../modeling/browse-and-rearrange-code-maps.md).  
  
##  <a name="MapStack"></a> Mapper la pile des appels  
  
1.  Démarrez le débogage.  \(Raccourci clavier : **F5**\)  
  
2.  Dès que votre application passe en mode arrêt ou que vous exécutez pas à pas une fonction, choisissez **Carte du code**.  \(Clavier : **Ctrl** \+ **Maj** \+ **\`**\)  
  
     ![Choisir Carte du code pour démarrer le mappage de la pile d'appels](../debugger/media/debuggermap_choosecodemap.png "DebuggerMap\_ChooseCodeMap")  
  
     La pile d'appels actuelle apparaît en orange sur une nouvelle carte de code :  
  
     ![Voir pile d'appels sur carte du code](../debugger/media/debuggermap_seeundocallstack.png "DebuggerMap\_SeeUndoCallStack")  
  
     La carte se mettra à jour automatiquement pendant que vous continuez le débogage.  Consultez [Mettre à jour la carte avec la pile d'appels suivante](#UpdateMap).  
  
##  <a name="MakeNotes"></a> Rédiger des notes sur le code  
 Ajoutez des commentaires pour effectuer le suivi de ce qui se passe dans le code.  Pour ajouter une nouvelle ligne dans des commentaires, appuyez sur **Maj \+ Entrée**.  
  
 ![Ajouter un commentaire à la pile d'appels sur le code de mappage](../debugger/media/debuggermap_addcomment.png "DebuggerMap\_AddComment")  
  
##  <a name="UpdateMap"></a> Mettre à jour la carte avec la pile d'appels suivante  
 Exécutez votre application jusqu'au point d'arrêt suivant ou exécutez pas à pas une fonction.  La carte ajoute une nouvelle pile d'appels.  
  
 ![Mettre à jour le Code de mappage avec la pile d'appels suivante](../debugger/media/debuggermap_addclearcallstack.png "DebuggerMap\_AddClearCallStack")  
  
##  <a name="AddRelatedCode"></a> Ajouter du code associé à la carte  
 Vous disposez désormais d'une carte, mais comment continuer ?  Si vous utilisez Visual C\# .NET ou Visual Basic .NET, ajoutez des éléments, tels que des champs, des propriétés et d'autres méthodes, pour suivre ce qui se passe dans le code.  
  
 Double\-cliquez sur une méthode pour afficher sa définition de code ou utilisez le menu contextuel pour la méthode.  \(Clavier : sélectionnez la méthode sur la carte et appuyez sur **F12**.\)  
  
 ![Aller à la définition du code pour une méthode sur une carte du code](../debugger/media/debuggermap_gotocodedefinition.png "DebuggerMap\_GoToCodeDefinition")  
  
 Ajoutez les éléments que vous souhaitez suivre sur la carte.  
  
 ![Afficher les champs dans une méthode sur la carte du code de la pile d’appels](../debugger/media/debuggermap_showfields.png "DebuggerMap\_ShowFields")  
  
> [!NOTE]
>  Par défaut, l'ajout d'éléments à la carte ajoute également les nœuds des groupes parents, comme la classe, l'espace de noms et l'assembly.  Bien que ceci soit utile, vous pouvez conserver la carte simple en désactivant cette fonctionnalité à l'aide du bouton **Inclure les parents** sur la barre d'outils de la carte, ou en appuyant sur **Ctrl** quand vous ajoutez des éléments.  
  
 ![Champs associés à une méthode sur la carte du code de la pile d'appels](../debugger/media/debuggermap_showedfields.png "DebuggerMap\_ShowedFields")  
  
 Vous pouvez ici voir aisément quelles méthodes utilisent les mêmes champs.  Les derniers éléments ajoutés apparaissent en vert.  
  
 Poursuivez l'élaboration de la carte pour afficher davantage de code.  
  
 ![Voir les méthodes qui utilisent un champ : carte du code de la pile des appels](../debugger/media/debuggermap_findallreferences.png "DebuggerMap\_FindAllReferences")  
  
 ![Méthodes qui utilisent un champ sur la carte du code de la pile d'appels](../debugger/media/debuggermap_foundallreferences.png "DebuggerMap\_FoundAllReferences")  
  
##  <a name="FindBugs"></a> Rechercher des bogues à l'aide de la carte  
 La visualisation de votre code peut vous aider à rechercher des bogues plus rapidement.  Par exemple, supposons que vous recherchiez un bogue dans un programme de dessin.  Lorsque vous tracez une ligne et essayez de l'annuler, rien ne se produit jusqu'à ce que vous traciez une autre ligne.  
  
 Vous définissez donc des points d'arrêt dans les méthodes `clear`, `undo` et `Repaint`, vous démarrez le débogage et vous générez une carte comme celle\-ci :  
  
 ![Ajouter une autre pile d'appels au code de mappage](../debugger/media/debuggermap_addpaintobjectcallstack.png "DebuggerMap\_AddPaintObjectCallStack")  
  
 Vous constatez que tous les mouvements de l'utilisateur sur la carte appellent `Repaint`, à l'exception de `undo`.  Cela peut expliquer pourquoi `undo` ne fonctionne pas immédiatement.  
  
 Après avoir corrigé le bogue et poursuivi l'exécution du programme, la carte ajoute le nouvel appel de `undo` à `Repaint` :  
  
 ![Ajouter un nouvel appel de méthode à la pile d'appels sur le code de mappage](../debugger/media/debuggermap_addnewcallforrepaint.png "DebuggerMap\_AddNewCallForRepaint")  
  
##  <a name="QA"></a> Q et R  
  
-   **Tous les appels n'apparaissent pas sur la carte.  Pourquoi ?**  
  
     Par défaut, seul votre propre code apparaît sur la carte.  Pour afficher le code externe, activez\-le dans la fenêtre **Pile des appels** :  
  
     ![Afficher du code externe à l'aide de la fenêtre Pile des appels](../debugger/media/debuggermap_callstackmenu.png "DebuggerMap\_CallStackMenu")  
  
     ou désactivez **Activer Uniquement mon Code** dans les options de débogage de Visual Studio :  
  
     ![Afficher du code externe à l'aide de la boîte de dialogue Options](../debugger/media/debuggermap_debugoptions.png "DebuggerMap\_DebugOptions")  
  
-   **La modification de la carte affecte\-t\-elle le code ?**  
  
     La modification de la carte n'affecte en aucune manière le code.  N'hésitez pas à renommer, déplacer ou supprimer tout élément de la carte.  
  
-   **Que signifie le message « Le diagramme peut être basé sur une version antérieure du code » ?**  
  
     Il se peut que le code ait changé après la dernière mise à jour de la carte.  Par exemple, un appel sur la carte peut ne plus exister dans le code.  Fermez le message et essayez de régénérer la solution avant de remettre à jour la carte.  
  
-   **Comment contrôler la disposition de la carte ?**  
  
     Ouvrez le menu **Disposition** dans la barre d'outils de la carte :  
  
    -   Modifiez la disposition par défaut.  
  
    -   Pour arrêter la réorganisation automatique de la carte, désactivez **Disposer automatiquement lors du débogage**.  
  
    -   Pour réorganiser la carte le moins possible lorsque vous ajoutez des éléments, désactivez **Disposition incrémentielle**.  
  
-   **Puis\-je partager la carte avec d'autres ?**  
  
     Vous pouvez exporter la carte, l'envoyer à d'autres personnes si vous disposez de Microsoft Outlook ou l'enregistrer dans votre solution afin de pouvoir la vérifier dans le contrôle de version Team Foundation.  
  
     ![Partager la carte du code de la pile d'appels avec les autres](../debugger/media/debuggermap_sharewithothers.png "DebuggerMap\_ShareWithOthers")  
  
-   **Comment puis\-je arrêter l'ajout automatique de nouvelles piles d'appels par la carte ?**  
  
     Choisissez ![Bouton &#45; Afficher la pile des appels sur le code de mappage automatiquement](../debugger/media/debuggermap_automaticupdateicon.png "DebuggerMap\_AutomaticUpdateIcon") dans la barre d'outils de la carte.  Pour ajouter manuellement la pile d'appels actuelle à la carte, appuyez sur **Ctrl** \+ **Maj** \+ **\`**.  
  
     La carte continuera de mettre en surbrillance les piles d'appels existantes sur la carte pendant le débogage.  
  
-   **Que signifient les flèches et les icônes d'élément ?**  
  
     Pour obtenir plus d'informations sur un élément, placez le pointeur de la souris sur celui\-ci et consultez l'info\-bulle.  Vous pouvez également examiner la **Légende** pour découvrir la signification de chaque icône.  
  
     ![Que signifient les icônes sur la carte du code de la pile d’appels ?](../debugger/media/debuggermap_showlegend.png "DebuggerMap\_ShowLegend")  
  
 Voir : [Mapper la pile des appels](#MapStack) • [Rédiger des notes sur le code](#MakeNotes) • [Mettre à jour la carte avec la pile d'appels suivante](#UpdateMap) • [Ajouter du code associé à la carte](#AddRelatedCode) • [Rechercher des bogues à l'aide de la carte](#FindBugs)  
  
## Voir aussi  
 [Map dependencies across your solutions](../modeling/map-dependencies-across-your-solutions.md)   
 [Use code maps to debug your applications](../modeling/use-code-maps-to-debug-your-applications.md)   
 [Rechercher des problèmes potentiels à l’aide des analyseurs de carte du code](../modeling/find-potential-problems-using-code-map-analyzers.md)   
 [Browse and rearrange code maps](../modeling/browse-and-rearrange-code-maps.md)