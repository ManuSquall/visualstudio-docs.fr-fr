---
title: 'CA1813 : Évitez les attributs unsealed | Microsoft Docs'
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
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c422e4e261374d591acd0630f428f139b29cfcca
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589994"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813 : Évitez les attributs unsealed
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1813 : Évitez les attributs unsealed](https://docs.microsoft.com/visualstudio/code-quality/ca1813-avoid-unsealed-attributes).

|||
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Category|Microsoft.Performance|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public hérite <xref:System.Attribute?displayProperty=fullName>, n’est pas abstrait et n’est pas scellé (`NotInheritable` en Visual Basic).

## <a name="rule-description"></a>Description de la règle
 La bibliothèque de classes du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] fournit des méthodes pour récupérer des attributs personnalisés. Par défaut, ces méthodes recherchent la hiérarchie d’héritage attribut ; par exemple <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> recherche le type d’attribut spécifié ou n’importe quel type d’attribut qui étend le type d’attribut spécifié. Le fait de sceller l’attribut élimine la recherche dans la hiérarchie d’héritage et peut améliorer les performances.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, scellez le type d’attribut ou rendre abstraite.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle. Vous devez le faire uniquement si vous définissez une hiérarchie d’attribut et ne peut pas sceller l’attribut ou rendre abstraite.

## <a name="example"></a>Exemple
 L’exemple suivant montre un attribut personnalisé qui satisfait cette règle.

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/cs/FxCop.Performance.AttributesSealed.cs#1)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/vb/FxCop.Performance.AttributesSealed.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1019 : Définissez des accesseurs pour les arguments d’attribut](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018 : Marquez les attributs avec AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Voir aussi
 [Attributs](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)



