---
title: 'CA1413 : Éviter les champs non publics dans les types valeur visibles par COM | Microsoft Docs'
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
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 86ab9f367e2fa9a8825527f8ec53ccfca5b67271
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238510"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413 : Éviter les champs non publics dans les types valeur visibles par COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Category|Microsoft.Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type valeur qui est marqué spécifiquement comme visible pour COM Component Object Model () déclare un champ d’instance non publics.

## <a name="rule-description"></a>Description de la règle
 Les champs d'instance non publics des types valeur visibles par COM sont visibles par les clients COM. Passez en revue le contenu du champ pour plus d’informations qui ne doivent pas être exposées et qui aura un effet de conception ou de sécurité involontaire.

 Par défaut, tous les types valeur publics sont visibles par COM. Toutefois, pour réduire les faux positifs, cette règle requiert que la visibilité COM du type d’être explicitement spécifié. L’assembly conteneur doit être marqué avec le <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> définie sur `false` et le type doit être marqué avec le <xref:System.Runtime.InteropServices.ComVisibleAttribute> défini sur `true`.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle et garder le champ masqué, modifier le type de valeur à un type référence ou de supprimer le <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribut à partir du type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si l’exposition publique du champ est acceptable.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole la règle.

 [!code-csharp[FxCop.Interoperability.NonpublicField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/cs/FxCop.Interoperability.NonpublicField.cs#1)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.NonpublicField/vb/FxCop.Interoperability.NonpublicField.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1407 : Éviter les membres statiques dans les types visibles par COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017 : Marquez les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Voir aussi
 [Interopérabilité avec du Code non managé](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [qualification des Types .NET pour l’interopérabilité](http://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd)



