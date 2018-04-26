---
title: 'CA1403 : Les types Structurer automatiquement ne doivent pas être visibles par COM'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 056b1d254b8544f9a1f0abe364bcb40f15235e64
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403 : Les types Structurer automatiquement ne doivent pas être visibles par COM
|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Category|Microsoft.Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type de valeur visible du modèle COM (Component Object) est marqué avec la <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> attribut la valeur <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 <xref:System.Runtime.InteropServices.LayoutKind> types de mise en page sont gérés par le common language runtime. La disposition de ces types peut varier entre les versions du .NET Framework, qui bloque les clients COM qui attendent une disposition spécifique. Notez que si le <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribut n’est pas spécifié, le langage c#, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], et les compilateurs C++ spécifient la <xref:System.Runtime.InteropServices.LayoutKind> disposition pour les types valeur.

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
 [Qualifier des Types .NET pour l’interopérabilité](/dotnet/framework/interop/qualifying-net-types-for-interoperation) [interopération avec du Code non managé](/dotnet/framework/interop/index)