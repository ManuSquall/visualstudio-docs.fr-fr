---
title: "CA1405&#160;: Les types de base type visibles par COM doivent &#234;tre visibles par COM | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1405"
  - "ComVisibleTypeBaseTypesShouldBeComVisible"
helpviewer_keywords: 
  - "CA1405"
  - "ComVisibleTypeBaseTypesShouldBeComVisible"
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1405&#160;: Les types de base type visibles par COM doivent &#234;tre visibles par COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|  
|CheckId|CA1405|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|DependsOnFix|  
  
## Cause  
 Un type COM \(Component Object Model\) visible dérive d'un type qui n'est pas un COM visible.  
  
## Description de la règle  
 Lorsqu'un type visible par COM ajoute des membres dans une nouvelle version, il doit se conformer strictement aux instructions pour éviter de bloquer des clients COM qui se lient à la version actuelle.  Un type qui est invisible dans COM suppose qu'il n'a pas besoin de respecter ces règles de contrôle de version COM lorsqu'il ajoute de nouveaux membres.  Toutefois, si un type visible par COM dérive du type invisible par COM et expose une interface de classe de <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.ClassInterfaceType> \(valeur par défaut\), tous les membres publics du type de base \(sauf s'ils sont marqués spécifiquement comme étant invisibles par COM, auquel cas, ils sont redondants\) sont exposés dans COM.  Si le type de base ajoute de nouveaux membres dans une version suivante, les clients COM qui se lient à l'interface de classe du type dérivé peuvent être bloqués.  Les types visibles par COM doivent dériver uniquement de types visibles par COM pour éviter toute possibilité de blocage des clients COM.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, faites en sorte que les types de base soient visibles par COM ou que le type dérivé soit invisible par COM.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant présente un type qui enfreint la règle.  
  
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-cs[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>   
 [Introducing the Class Interface](http://msdn.microsoft.com/fr-fr/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)