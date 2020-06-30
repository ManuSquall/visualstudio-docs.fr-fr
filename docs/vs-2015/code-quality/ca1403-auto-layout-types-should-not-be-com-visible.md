---
title: 'CA1403 : les types de disposition automatique ne doivent pas être visibles par COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1752efb5be1828f62703e1fe1a1130b37ff80503
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534925"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403 : Les types Structurer automatiquement ne doivent pas être visibles par COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type valeur visible COM (Component Object Model) est marqué avec l' <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> attribut défini sur <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName> .

## <a name="rule-description"></a>Description de la règle
 <xref:System.Runtime.InteropServices.LayoutKind>les types de disposition sont gérés par le common language runtime. La disposition de ces types peut changer d’une version à l’autre de la .NET Framework, ce qui va rompre les clients COM qui attendent une disposition spécifique. Notez que si l' <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribut n’est pas spécifié, les [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compilateurs C#, et C++ spécifient la <xref:System.Runtime.InteropServices.LayoutKind> disposition des types valeur.

 Sauf indication contraire, tous les types non génériques publics sont visibles par COM ; tous les types non publics et génériques sont invisibles pour COM. Toutefois, pour réduire les faux positifs, cette règle exige que la visibilité COM du type soit explicitement indiquée. l’assembly conteneur doit être marqué avec le <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> défini sur `false` et le type doit être marqué avec le <xref:System.Runtime.InteropServices.ComVisibleAttribute> défini sur `true` .

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez la valeur de l' <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribut par <xref:System.Runtime.InteropServices.LayoutKind> ou <xref:System.Runtime.InteropServices.LayoutKind> , ou rendez le type invisible pour com.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole la règle et un type qui satisfait la règle.

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1408 : Ne pas utiliser le paramètre AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Voir aussi
 [Présentation](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) des [types .net éligibles de l’interface de classe pour l’interopérabilité entre l’interopérabilité](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [et le code non managé](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
