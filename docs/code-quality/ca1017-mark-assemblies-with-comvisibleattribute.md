---
title: "CA1017&#160;: Marquer les assemblys avec ComVisibleAttribute | Microsoft Docs"
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
  - "CA1017"
  - "MarkAssembliesWithComVisible"
helpviewer_keywords: 
  - "MarkAssembliesWithComVisible"
  - "CA1017"
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1017&#160;: Marquer les assemblys avec ComVisibleAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithComVisible|  
|CheckId|CA1017|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un assembly ne se voit pas appliquer l'attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>.  
  
## Description de la règle  
 L'attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> détermine comment les clients COM accèdent à du code managé.  Un bon design stipule que les assemblys indiquent explicitement la visibilité COM.  La visibilité COM peut être définie pour un assembly en entier, puis être substituée pour des types et des membres de type individuels.  Si l'attribut n'est pas présent, les clients COM peuvent voir le contenu de l'assembly.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez l'attribut à l'assembly.  Si vous ne souhaitez pas que les clients COM puissent voir l'assembly, appliquez l'attribut et affectez\-lui la valeur `false`.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  Si vous souhaitez que l'assembly soit visible, appliquez\-le et affectez\-lui la valeur `true`.  
  
## Exemple  
 L'exemple suivant montre un assembly qui se voit appliquer l'attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> pour empêcher les clients COM de le voir.  
  
 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-cs[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]  
  
## Voir aussi  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)