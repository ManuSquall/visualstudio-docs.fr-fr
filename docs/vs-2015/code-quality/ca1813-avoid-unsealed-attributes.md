---
title: 'CA1813 : Évitez les attributs non scellés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fe5967ef099794b6c71029e9d03d959dd83b01dc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647053"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813 : Évitez les attributs unsealed
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Category|Microsoft. performance|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public hérite de <xref:System.Attribute?displayProperty=fullName>, n’est pas abstrait et n’est pas sealed (`NotInheritable` dans Visual Basic).

## <a name="rule-description"></a>Description de la règle
 La bibliothèque de classes du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] fournit des méthodes pour récupérer des attributs personnalisés. Par défaut, ces méthodes recherchent la hiérarchie d’héritage d’attribut ; par exemple <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> recherche le type d’attribut spécifié, ou tout type d’attribut qui étend le type d’attribut spécifié. La fermeture de l’attribut élimine la recherche dans la hiérarchie d’héritage et peut améliorer les performances.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, scellez le type d’attribut ou rendez-le abstrait.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle. Vous ne devez effectuer cette opération que si vous définissez une hiérarchie d’attribut et que vous ne pouvez pas sceller l’attribut ou le rendre abstrait.

## <a name="example"></a>Exemple
 L’exemple suivant montre un attribut personnalisé qui satisfait cette règle.

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/cs/FxCop.Performance.AttributesSealed.cs#1)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/vb/FxCop.Performance.AttributesSealed.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1019 : Définissez des accesseurs pour les arguments d’attribut](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018 : Marquez les attributs avec AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Voir aussi
 [Attributs](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
