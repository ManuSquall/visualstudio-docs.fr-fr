---
title: "Impossible de d&#233;terminer si &#39;assembly&#39; est un assembly multifichier. Le manifeste d’assembly est peut-&#234;tre endommag&#233;. L’assembly est suppos&#233; ne pas &#234;tre un assembly multifichier. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.unknownscatterstatusforcopy"
ms.assetid: be49d3f2-b091-488c-8579-e27ef09d9c80
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Impossible de d&#233;terminer si &#39;assembly&#39; est un assembly multifichier. Le manifeste d’assembly est peut-&#234;tre endommag&#233;. L’assembly est suppos&#233; ne pas &#234;tre un assembly multifichier.
Le système de projet n’a pas pu accéder à un assembly référencé par votre projet et ne peut donc pas déterminer si vous faites référence à un assembly multifichier. Cela peut empêcher l’assembly d’être copié correctement dans le répertoire de sortie.  
  
 **Pour corriger cette erreur**  
  
-   Réinstallez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(si l’assembly a été fourni avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ou le .NET Framework\).  
  
     ou  
  
-   Réinstallez le contrôle tiers approprié.  
  
     Cette erreur n’empêche pas la création du projet. Toutefois, une erreur d’exécution est possible.  
  
## Voir aussi  
 [Dépannage de références rompues](../ide/troubleshooting-broken-references.md)   
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Assemblies in the Common Language Runtime](http://msdn.microsoft.com/fr-fr/33a0bc6a-6bb3-44c7-ada7-4a046e8c0945)