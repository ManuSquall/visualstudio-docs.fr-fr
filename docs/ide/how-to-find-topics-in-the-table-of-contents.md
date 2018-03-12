---
title: "Utiliser la table des matières de Help Viewer dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-help-viewer
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- hv_contents
helpviewer_keywords:
- Help Viewer, table of contents filtering
- Help Viewer, Contents tab
- Contents tab [Help Viewer]
- table of contents filtering [Help Viewer]
ms.assetid: 8b98464d-2b05-4710-ad68-5647e78c6b7b
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fdb49d915871bd9ac955ed61cdc7850bf35d6f41
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-topics-in-the-table-of-contents"></a>Guide pratique pour rechercher des rubriques dans la table des matières
Sous l’onglet **Sommaire**, vous pouvez utiliser la table des matières pour rechercher des informations. La table des matières est une liste pouvant être développée qui contient toutes les rubriques des livres installés. Pour des informations d’accessibilité relatives à la navigation dans la table des matières, consultez [Touches de raccourci (Help Viewer)](../ide/shortcut-keys-help-viewer.md).  
  
> [!IMPORTANT]
>  Le nombre de rubriques disponibles dans la table des matières dépend du filtre que vous avez sélectionné.  
  
## <a name="filter-the-toc"></a>Filtrer la table des matières  
Vous pouvez filtrer la table des matières pour réduire le nombre de rubriques qui s’affichent sous l’onglet **Sommaire**. Les titres apparaissent dans la liste que s'ils contiennent la racine du terme que vous spécifiez. Par exemple, si vous spécifiez le filtre « configurer », seuls les titres qui contiennent « configure » ou « configurer » s'affichent. Les nœuds dont les titres ne contiennent pas le terme sont réduits à un seul nœud avec des points de suspension (...).  
  
#### <a name="to-filter-the-toc"></a>Pour filtrer la table des matières  
  
1.  Choisissez l’onglet **Sommaire**.  
  
2.  Dans la zone de texte **Filtrer le contenu**, entrez un terme.  
  
> [!NOTE]
>  Si le filtre met trop longtemps à s’exécuter, vous pouvez afficher les résultats plus rapidement à l’aide de l’opérateur de recherche avancé `title:`.  
  
## <a name="synchronize-a-topic-with-the-toc"></a>Synchroniser une rubrique avec la table des matières  
Si vous avez ouvert une rubrique à l'aide des fonctionnalités d'index ou de recherche en texte intégral, vous pouvez localiser cette rubrique dans la table des matières en synchronisant celle-ci avec la fenêtre de la rubrique.
  
#### <a name="to-synchronize-the-toc-with-the-topic-window"></a>Pour synchroniser la table des matières avec la fenêtre de rubrique  
  
1.  Affichez une rubrique.  
  
2.  Cliquez sur le bouton **Afficher une rubrique dans le sommaire** dans la barre d’outils ou appuyez sur **Ctrl + S**.  
  
     L’onglet **Sommaire** s’ouvre et affiche l’emplacement de la rubrique dans la table des matières.  
  
## <a name="see-also"></a>Voir aussi
[Guide pratique pour rechercher des rubriques dans l’index](../ide/how-to-find-topics-in-the-index.md)  
[Guide pratique pour rechercher des rubriques](../ide/how-to-search-for-topics.md)  
[Microsoft Help Viewer](../ide/microsoft-help-viewer.md)