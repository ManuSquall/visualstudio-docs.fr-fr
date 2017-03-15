---
title: "CA1014&#160;: Marquer les assemblys avec CLSCompliantAttribute | Microsoft Docs"
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
  - "CA1014"
  - "MarkAssembliesWithClsCompliant"
helpviewer_keywords: 
  - "CA1014"
  - "MarkAssembliesWithClsCompliant"
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1014&#160;: Marquer les assemblys avec CLSCompliantAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithClsCompliant|  
|CheckId|CA1014|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un assembly ne se voit pas appliquer l'attribut <xref:System.CLSCompliantAttribute?displayProperty=fullName>.  
  
## Description de la règle  
 La spécification de langage commun CLS \(Common Language Specification\) définit des restrictions de dénomination, des types de données, et des règles auxquelles les assemblys doivent se conformer s'ils doivent être utilisés à l'échelle de différents langages de programmation.  Un design correct stipule que tous les assemblys indiquent explicitement la conformité CLS avec <xref:System.CLSCompliantAttribute>.  Si l'attribut n'est pas présent sur un assembly, l'assembly n'est pas conforme.  
  
 Un assembly conforme CLS peut contenir des types ou des membres de type non conformes.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez l'attribut à l'assembly.  Au lieu de marquer l'ensemble de l'assembly comme non conforme, vous devez déterminer quels type ou membres de type sont non conformes et marquer ces éléments comme tel.  Si possible, vous devez fournir une solution de substitution conforme CLS aux membres non conformes afin que l'audience la plus large possible puisse accéder à toutes les fonctionnalités de votre assembly.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  Si vous ne souhaitez pas que l'assembly soit conforme, appliquez l'attribut et affectez\-lui la valeur `false`.  
  
## Exemple  
 L'exemple suivant présente un assembly auquel est appliqué l'attribut <xref:System.CLSCompliantAttribute?displayProperty=fullName> qui le déclare comme étant conforme CLS.  
  
 [!code-cs[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]  
  
## Voir aussi  
 <xref:System.CLSCompliantAttribute?displayProperty=fullName>   
 [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)