---
title: 'CA1406 : éviter les arguments Int64 pour les clients Visual Basic 6 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b6ab93c24cd97d498ae886c7a9184fd4a5f111f1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534912"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406 : Éviter les arguments Int64 pour les clients Visual Basic 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type qui est spécifiquement marqué comme visible par le modèle COM (Component Object Model) déclare un membre qui accepte un <xref:System.Int64?displayProperty=fullName> argument.

## <a name="rule-description"></a>Description de la règle
 Les clients COM Visual Basic 6 ne peuvent pas accéder aux entiers de 64 bits.

 Par défaut, les éléments suivants sont visibles par COM : assemblys, les types publics, les membres d’instance publics dans les types publics et tous les membres des types valeur publics. Toutefois, pour réduire les faux positifs, cette règle exige que la visibilité COM du type soit explicitement indiquée. l’assembly conteneur doit être marqué avec le <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> défini sur `false` et le type doit être marqué avec le <xref:System.Runtime.InteropServices.ComVisibleAttribute> défini sur `true` .

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle pour un paramètre dont la valeur peut toujours être exprimée sous la forme d’un entier 32 bits, remplacez le type de paramètre par <xref:System.Int32?displayProperty=fullName> . Si la valeur du paramètre peut être supérieure à celle qui peut être exprimée sous la forme d’un entier 32 bits, remplacez le type de paramètre par <xref:System.Decimal?displayProperty=fullName> . Notez que <xref:System.Single?displayProperty=fullName> et <xref:System.Double?displayProperty=fullName> perdent la précision aux plages supérieures du type de <xref:System.Int64> données. Si le membre n’est pas destiné à être visible par COM, marquez-le avec la <xref:System.Runtime.InteropServices.ComVisibleAttribute> valeur `false` .

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle s’il est certain que Visual Basic 6 clients COM n’accèdent pas au type.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole la règle.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/cs/FxCop.Interoperability.LongArgument.cs#1)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/vb/FxCop.Interoperability.LongArgument.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1413 : Éviter les champs non publics dans les types valeur visibles par COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407 : Éviter les membres statiques dans les types visibles par COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017 : Marquer les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Voir aussi
 Interopérabilité avec le [type de données long](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516) du [code non managé](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
