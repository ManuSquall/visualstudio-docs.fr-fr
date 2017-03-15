---
title: "Erreur MSBuild MSB3253 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB3253"
ms.assetid: d4b5eb5b-703b-4b80-aa5d-6c70ff9fe84d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Erreur MSBuild MSB3253
**MSB3254 : L'assembly \<nom\> référencé dans le projet dépend de \<nom2\> qui n'est pas contenu dans le .NET Framework Client Profile.**  
  
 Un des assemblys ou des assemblys dépendants référencé dans le projet dépend d'un autre assembly qui n'est pas contenu dans le [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)].  
  
 En général, ce message apparaît lorsqu'un projet référence une DLL ou un contrôle tiers qui référence un assembly externe.  Par exemple, un projet utilise un contrôle qui utilise ensuite une fonctionnalité contenue dans le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] complet.  Si l'application est de nouveau ciblée pour le [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] et installée sur un système qui n'a pas le [!INCLUDE[net_v35_long](../misc/includes/net_v35_long_md.md)], l'application peut ne pas fonctionner correctement si elle tente d'accéder à une fonctionnalité non contenue dans le sous\-ensemble [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)].  
  
 Ce message « d'erreur » n'est en fait qu'un avertissement car l'application continue de compiler.  Toutefois, l'application peut échouer ultérieurement si le contrôle ou la DLL fait référence à une fonctionnalité située dans un assembly manquant.  
  
 Le [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)] est un sous\-ensemble de la bibliothèque runtime [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 3.5 complète.  Pour plus d'informations sur le [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)], consultez [.NET Framework Client Profile](../Topic/.NET%20Framework%20Client%20Profile.md).  
  
### Pour corriger cette erreur  
  
-   Supprimez la référence d'assembly spécifiée du projet ou ciblez le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] complet plutôt que la bibliothèque du sous\-ensemble [!INCLUDE[net_client_v35_long](../misc/includes/net_client_v35_long_md.md)].  Pour plus d'informations sur la façon de cibler le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] complet, consultez [Comment : cibler une version du .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
## Voir aussi  
 [Target Framework and Target Platform](../msbuild/msbuild-target-framework-and-target-platform.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)