---
title: 'CA1403 : Les types Structurer automatiquement ne doivent pas être visibles par COM | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5051b784c1e7fe239ceec4fc0e1856765ce6f57f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588051"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403 : Les types Structurer automatiquement ne doivent pas être visibles par COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1403 : les types Structurer automatiquement ne doivent pas être visibles par COM](https://docs.microsoft.com/visualstudio/code-quality/ca1403-auto-layout-types-should-not-be-com-visible).

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Category|Microsoft.Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type de valeur visible du composant COM (Object Model) est marqué avec le <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> attribut la valeur <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 <xref:System.Runtime.InteropServices.LayoutKind> les types de disposition sont gérés par le common language runtime. La disposition de ces types peut varier entre les versions du .NET Framework, ce qui bloque les clients COM qui attendent une disposition spécifique. Notez que si le <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribut n’est pas spécifié, le c#, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], et spécifient les compilateurs C++ le <xref:System.Runtime.InteropServices.LayoutKind> disposition pour les types valeur.

 Sauf mention contraire, tous les types non génériques publics sont visibles par COM ; tous les types non publics et génériques ne sont pas visibles par COM. Toutefois, pour réduire les faux positifs, cette règle requiert que la visibilité COM du type d’être explicitement spécifié ; l’assembly conteneur doit être marqué avec le <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> définie sur `false` et le type doit être marqué avec le <xref:System.Runtime.InteropServices.ComVisibleAttribute> défini sur `true`.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez la valeur de la <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribut <xref:System.Runtime.InteropServices.LayoutKind> ou <xref:System.Runtime.InteropServices.LayoutKind>, ou rendez le type invisible à COM.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole la règle et un type qui satisfait la règle.

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1408 : N’utilisez pas le paramètre AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Voir aussi
 [Présentation de l’Interface de classe](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024) [qualification des Types .NET pour l’interopérabilité](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [interopération avec du Code non managé](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



