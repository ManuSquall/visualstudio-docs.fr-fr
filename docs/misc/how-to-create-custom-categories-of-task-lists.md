---
title: "Proc&#233;dure&#160;: cr&#233;ation de cat&#233;gories personnalis&#233;es de Listes des t&#226;ches | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Liste des tâches, catégories personnalisées"
ms.assetid: 5e4ac1b1-9afb-46c5-9dcc-6cab9c5ceee8
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Proc&#233;dure&#160;: cr&#233;ation de cat&#233;gories personnalis&#233;es de Listes des t&#226;ches
Les catégories personnalisées de tâches fournissent le contrôle de la façon dont les tâches sont affichées dans la fenêtre de **Liste des tâches** .  
  
 implémentez une catégorie personnalisée de tâches pour les raisons suivantes :  
  
-   Vous souhaitez contrôler où vos catégories sont affichées \(trié\) dans la liste des catégories.  
  
-   Vous avez plusieurs sous\-catégories de tâches que vous souhaitez trier dans une catégorie sans autres tâches tri entre elles.  
  
-   Vous souhaitez créer une vue personnalisée dans laquelle seules vos tâches sont affichées.  
  
    > [!NOTE]
    >  Vous pouvez obtenir des effets similaires aux catégories personnalisées sans implémenter en fait une catégorie personnalisée.  Par exemple, vous pouvez afficher une bitmap pour une catégorie ou la sous\-catégorie en implémentant <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2.ImageList%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem2.ImageListIndex%2A>.  Le fournisseur de tâche fournit la liste puis chaque tâche fournit un index dans la liste.  
  
 Pour créer une catégorie personnalisée dans **Liste des tâches**, stockez \-la avec **Liste des tâches** à l'aide de la procédure suivante.  
  
### pour enregistrer une catégorie personnalisée de liste des tâches  
  
-   Appelez l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterCustomCategory%2A> pour stocker une catégorie personnalisée à la liste des tâches.  
  
     chaque catégorie personnalisée doit avoir son propre GUID, qui est spécifiée dans le paramètre d' `guidCat` .  Dans le paramètre d' `dwSortOrder` , indiquez l'emplacement où vous souhaitez que cette catégorie la trie \(lorsque la liste est triée par catégories\).  Cette méthode retourne ensuite le positionnement de tri réel de la catégorie personnalisée dans la liste plus grande de catégories.  
  
     les ordres de tri pour les catégories prédéfinies de tâche, qui sont définies dans l'énumération d' <xref:Microsoft.VisualStudio.Shell.Interop.VSTASKCATEGORY> , sont dans le tableau suivant.  
  
    |Catégorie|Valeur|Description|  
    |---------------|------------|-----------------|  
    |CAT\_ALL|1|Pas une véritable catégorie.  Utilisé pour permettre à une vue de liste des tâches pour afficher toutes les tâches dans **Liste des tâches**.|  
    |CAT\_BUILDCOMPILE|10|Erreurs de build, avertissements, et éventuellement erreurs de déploiement.|  
    |CAT\_COMMENTS|20|Tâches générées par des commentaires spéciaux, tels que « TODO », « ANNULÉ, » ou « HACK ».|  
    |CAT\_CODESENSE|30|Les erreurs générées lorsque vous tapez code source.|  
    |CAT\_SHORTCUTS|40|Raccourcis au codage.|  
    |CAT\_USER|50|Tâches entrées par l'utilisateur.|  
    |CAT\_MISC|60|Diverses tâches que les VSPackages souhaite à ajouter à **Liste des tâches**.|  
    |CAT\_HTML|70|Tâches relatives au développement de pages Web.|  
  
     Par exemple, pour inclure une catégorie entre CAT\_CODESENSE et CAT\_SHORTCUTS, vous pouvez passer dans une valeur de 31 pour votre ordre de tri.  Toutefois, comme une valeur de 31 peut déjà être utilisée par un autre fournisseur personnalisé de catégorie de tâche, **Liste des tâches** vous affecte que la catégorie de tâche pour le suivant substitue l'emplacement.  Cette valeur est retournée dans le paramètre d' `pCat` .  
  
### Pour annuler l'enregistrement d'une catégorie personnalisée de liste des tâches  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.UnregisterCustomCategory%2A> d'appel pour annuler l'enregistrement de votre catégorie personnalisée.  
  
## Voir aussi  
 [Création de vues de liste des tâches personnalisée](/visual-cpp/misc/creating-custom-task-list-views)