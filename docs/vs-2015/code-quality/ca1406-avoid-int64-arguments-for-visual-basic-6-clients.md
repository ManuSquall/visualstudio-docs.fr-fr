---
title: 'CA1406 : Éviter les arguments Int64 pour les clients Visual Basic 6 | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 81217588ab2f633ee7fc25d8036e7506a7de0364
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878334"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406 : Éviter les arguments Int64 pour les clients Visual Basic 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Category|Microsoft.Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type qui est marqué spécifiquement comme visible pour COM Component Object Model () déclare un membre qui accepte un <xref:System.Int64?displayProperty=fullName> argument.

## <a name="rule-description"></a>Description de la règle
 Les clients COM Visual Basic 6 ne peut pas accéder aux entiers de 64 bits.

 Par défaut, les éléments suivants sont visibles par COM : assemblys, types publics, membres d’instance publics dans les types publics et tous les membres de types valeur publics. Toutefois, pour réduire les faux positifs, cette règle requiert que la visibilité COM du type d’être explicitement spécifié ; l’assembly conteneur doit être marqué avec le <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> définie sur `false` et le type doit être marqué avec le <xref:System.Runtime.InteropServices.ComVisibleAttribute> défini sur `true`.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle pour un paramètre dont la valeur peut toujours être exprimée comme un entier 32 bits, modifiez le type de paramètre <xref:System.Int32?displayProperty=fullName>. Si la valeur du paramètre peut être supérieure peut être exprimée comme un entier 32 bits, remplacez le type de paramètre à <xref:System.Decimal?displayProperty=fullName>. Notez que les deux <xref:System.Single?displayProperty=fullName> et <xref:System.Double?displayProperty=fullName> une perte de précision dans les plages supérieures de la <xref:System.Int64> type de données. Si le membre n’est pas destiné à être visible par COM, marquez-le avec le <xref:System.Runtime.InteropServices.ComVisibleAttribute> défini sur `false`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle s’il est certain que les clients COM Visual Basic 6 n’accèdent pas le type.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole la règle.

 [!code-csharp[FxCop.Interoperability.LongArgument#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/cs/FxCop.Interoperability.LongArgument.cs#1)]
 [!code-vb[FxCop.Interoperability.LongArgument#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LongArgument/vb/FxCop.Interoperability.LongArgument.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1413 : Évitez les champs non publics dans les types valeur visibles par COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407 : Éviter les membres statiques dans les types visibles par COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017 : Marquez les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Voir aussi
 [Interopérabilité avec du Code non managé](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [Type de données Long](http://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516)



