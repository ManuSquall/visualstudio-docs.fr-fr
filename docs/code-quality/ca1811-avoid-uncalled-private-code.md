---
title: 'CA1811 : Évitez le recours à du code privé non appelé'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92a7542499eceeccbd62ce327b386dc099b726b2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233620"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811 : Évitez le recours à du code privé non appelé

|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Category|Microsoft. performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Un membre privé ou interne (au niveau de l’assembly) n’a pas d’appelants dans l’assembly, n’est pas appelé par le common language runtime et n’est pas appelé par un délégué. Les membres suivants ne sont pas vérifiés par cette règle :

- Membres d’interface explicites.

- Constructeurs statiques.

- Constructeurs de sérialisation.

- Méthodes marquées <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> avec <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>ou.

- Membres qui sont des substitutions.

## <a name="rule-description"></a>Description de la règle
Cette règle peut signaler des faux positifs si des points d’entrée qui ne sont pas actuellement identifiés par la logique de règle sont présents. En outre, un compilateur peut émettre du code non pouvant être appelé dans un assembly.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, supprimez le code pouvant être appelé ou ajoutez du code qui l’appelle.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle.

## <a name="related-rules"></a>Règles associées
[CA1812 Évitez les classes internes non instanciées](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801 Passer en revue les paramètres inutilisés](../code-quality/ca1801-review-unused-parameters.md)

[CA1804 Supprimer les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)