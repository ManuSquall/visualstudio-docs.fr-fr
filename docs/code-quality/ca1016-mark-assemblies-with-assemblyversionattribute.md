---
title: "CA1016&#160;: Marquer les assemblys avec AssemblyVersionAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MarkAssembliesWithAssemblyVersion"
  - "CA1016"
helpviewer_keywords: 
  - "CA1016"
  - "MarkAssembliesWithAssemblyVersion"
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1016&#160;: Marquer les assemblys avec AssemblyVersionAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithAssemblyVersion|  
|CheckId|CA1016|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 L'assembly n'a pas de numéro de version.  
  
## Description de la règle  
 L'identité d'un assembly est composée des informations suivantes :  
  
-   Nom de l'assembly  
  
-   Numéro de version  
  
-   Culture  
  
-   Clé publique \(pour les assemblys à nom fort\).  
  
 Le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] utilise le numéro de version pour identifier un assembly de manière unique, et créer une liaison avec des types présents dans des assemblys à nom fort.  Le numéro de version est utilisé conjointement avec la version et la stratégie d'éditeur.  Par défaut, les applications s'exécutent uniquement avec la version d'assembly avec laquelle elles ont été construites.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez un numéro de version à l'assembly à l'aide de l'attribut <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName>.  Voir l'exemple suivant.  
  
## Quand supprimer les avertissements  
 Ne supprimez pas d'avertissement de cette règle pour les assemblys utilisés par des tiers ou dans un environnement de production.  
  
## Exemple  
 L'exemple suivant montre un assembly auquel est appliqué l'attribut <xref:System.Reflection.AssemblyVersionAttribute>.  
  
 [!code-cs[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]  
  
## Voir aussi  
 [Versioning des assemblys](../Topic/Assembly%20Versioning.md)   
 [Comment : créer une stratégie d'éditeur](../Topic/How%20to:%20Create%20a%20Publisher%20Policy.md)