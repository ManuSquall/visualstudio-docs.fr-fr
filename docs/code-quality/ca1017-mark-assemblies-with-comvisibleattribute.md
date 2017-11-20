---
title: "CA1017 : Marquer les assemblys avec ComVisibleAttribute | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5e4c76efff009c85f9d607611d92d53cad5d2759
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017 : Marquer les assemblys avec ComVisibleAttribute
|||  
|-|-|  
|TypeName|MarkAssembliesWithComVisible|  
|CheckId|CA1017|  
|Catégorie|Microsoft.Design|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un assembly n’a pas la <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> attribut appliqué à celui-ci.  
  
## <a name="rule-description"></a>Description de la règle  
 Le <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribut détermine la façon dont les clients COM accèdent du code managé. Un bon design stipule que les assemblys indiquent explicitement la visibilité COM. La visibilité COM peut être définie pour un assembly entier et puis être substituée pour des types et membres de type. Si l’attribut n’est pas présent, le contenu de l’assembly est visible aux clients COM.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez l’attribut à l’assembly. Si vous ne souhaitez pas que l’assembly soit visible par les clients COM, appliquez l’attribut et définissez sa valeur sur `false`.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. Si vous souhaitez que l’assembly soit visible, appliquez l’attribut et définissez sa valeur sur `true`.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un assembly qui a le <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribut appliqué pour empêcher les clients COM.  
  
 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interopération avec du code non managé](/dotnet/framework/interop/index)   
 [Qualifier des types .NET pour l'interopérabilité](/dotnet/framework/interop/qualifying-net-types-for-interoperation)