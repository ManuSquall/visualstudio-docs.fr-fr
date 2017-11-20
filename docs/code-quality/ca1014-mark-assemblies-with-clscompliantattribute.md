---
title: "CA1014 : Marquer les assemblys avec CLSCompliantAttribute | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a870721f0bf7192b417d2105635c663fb69713c7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014 : Marquer les assemblys avec CLSCompliantAttribute
|||  
|-|-|  
|TypeName|MarkAssembliesWithClsCompliant|  
|CheckId|CA1014|  
|Catégorie|Microsoft.Design|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un assembly n’a pas la <xref:System.CLSCompliantAttribute?displayProperty=fullName> attribut appliqué à celui-ci.  
  
## <a name="rule-description"></a>Description de la règle  
 La spécification de langage commun CLS (Common Language Specification) définit des restrictions de dénomination, des types de données, et des règles auxquelles les assemblys doivent se conformer s'ils doivent être utilisés à l'échelle de différents langages de programmation. Design correct stipule que tous les assemblys indiquent explicitement la conformité CLS avec <xref:System.CLSCompliantAttribute>. Si l’attribut n’est pas présent sur un assembly, l’assembly n’est pas conforme.  
  
 Il est possible pour un assembly conforme CLS pour contiennent des types ou membres qui ne sont pas conformes.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez l’attribut à l’assembly. Au lieu de marquer l’intégralité de l’assembly comme non conforme, vous devez déterminer l’ou les membres de type ne sont pas conformes et marquer ces éléments comme tel. Si possible, vous devez fournir une alternative conforme CLS pour les membres non conformes afin que l’audience la plus large possible puisse accéder à toutes les fonctionnalités de votre assembly.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. Si vous ne souhaitez pas que l’assembly soit conforme, appliquez l’attribut et définissez sa valeur sur `false`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un assembly qui a le <xref:System.CLSCompliantAttribute?displayProperty=fullName> attribut appliqué qui déclare conformes à CLS.  
  
 [!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.CLSCompliantAttribute?displayProperty=fullName>   
 [Indépendance du langage et composants indépendants du langage](http://msdn.microsoft.com/Library/4f0b77d0-4844-464f-af73-6e06bedeafc6)