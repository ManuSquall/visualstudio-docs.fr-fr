---
title: "CA1405 : Les types base type visibles par COM doivent être visibles par COM | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 91634d5d46d63165874deded9c5ac67e7d4afa07
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405 : Les types de base type visibles par COM doivent être visibles par COM
|||  
|-|-|  
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|  
|CheckId|CA1405|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|DependsOnFix|  
  
## <a name="cause"></a>Cause  
 Un type visible du modèle COM (Component Object) dérive d’un type qui n’est pas visible par COM.  
  
## <a name="rule-description"></a>Description de la règle  
 Quand un type visible par COM ajoute des membres dans une nouvelle version, il doit se conformer aux recommandations strictes afin d’éviter l’interruption des clients COM qui se lient à la version actuelle. Un type qui est invisible dans COM suppose qu’il ne dispose pas de suivre ces règles de versioning COM lorsqu’il ajoute de nouveaux membres. Toutefois, si un visibles par COM type dérive du type invisible par COM et expose une interface de classe de <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.ClassInterfaceType> (la valeur par défaut), tous les membres publics du type de base (sauf si elles sont spécifiquement marquées comme COM invisibles, ce qui serait redondant) sont exposées à COM. Si le type de base ajoute de nouveaux membres dans une version ultérieure, les clients COM qui se lient à l’interface de classe du type dérivé peuvent interrompre. Types visibles par COM doivent dériver uniquement de types visibles par COM afin de réduire le risque d’interrompre les clients COM.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, rendez les types visibles par COM de base ou le type dérivé COM invisible.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type qui enfreint la règle.  
  
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>   
 [Présentation de l’interface de classe](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Interopération avec du code non managé](/dotnet/framework/interop/index)