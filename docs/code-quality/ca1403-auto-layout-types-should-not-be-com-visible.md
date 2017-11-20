---
title: "CA1403 : Les types Structurer automatiquement ne doivent pas être visibles par COM | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e5f8617b7ed5f0bec9ecaa2f4fbca1653cee46f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403 : Les types Structurer automatiquement ne doivent pas être visibles par COM
|||  
|-|-|  
|TypeName|AutoLayoutTypesShouldNotBeComVisible|  
|CheckId|CA1403|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type de valeur visible du modèle COM (Component Object) est marqué avec la <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> attribut la valeur <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Description de la règle  
 <xref:System.Runtime.InteropServices.LayoutKind>types de mise en page sont gérés par le common language runtime. La disposition de ces types peut varier entre les versions du .NET Framework, qui bloque les clients COM qui attendent une disposition spécifique. Notez que si le <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribut n’est pas spécifié, le langage c#, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], et les compilateurs C++ spécifient la <xref:System.Runtime.InteropServices.LayoutKind> disposition pour les types valeur.  
  
 Sauf mention contraire, tous les types non génériques publics sont visibles par COM ; tous les types génériques et non publics ne sont pas visibles par COM. Toutefois, pour réduire les faux positifs, cette règle requiert que la visibilité COM du type à être défini explicitement ; l’assembly conteneur doit être marqué avec le <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> la valeur `false` et le type doit être marqué avec le <xref:System.Runtime.InteropServices.ComVisibleAttribute> la valeur `true`.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez la valeur de la <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribut <xref:System.Runtime.InteropServices.LayoutKind> ou <xref:System.Runtime.InteropServices.LayoutKind>, ou rendez le type invisible à COM.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type qui enfreint la règle et un type qui satisfait la règle.  
  
 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1408 : N’utilisez pas le paramètre AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de l’interface de classe](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Qualification des types .NET pour l’interopérabilité](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [Interopération avec du code non managé](/dotnet/framework/interop/index)