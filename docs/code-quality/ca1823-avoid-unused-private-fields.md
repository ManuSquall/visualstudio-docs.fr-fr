---
title: 'CA1823 : Évitez les champs privés inutilisés'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47a2ad3b64055584551a63a2333e29286783d8cf
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921358"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823 : Évitez les champs privés inutilisés

|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Catégorie|Microsoft. performance|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Cette règle est signalée lorsqu’un champ privé de votre code existe mais n’est utilisé par aucun chemin d’accès de code.

## <a name="rule-description"></a>Description de la règle
Des champs privés qui ne sont pas accessibles dans l'assembly ont été détectés.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, supprimez le champ ou ajoutez du code qui l’utilise.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle.

## <a name="related-rules"></a>Règles associées
[CA1812 Évitez les classes internes non instanciées](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

[CA1801 Passer en revue les paramètres inutilisés](../code-quality/ca1801-review-unused-parameters.md)

[CA1804 Supprimer les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)

[CA1811 Éviter le code privé qui n’a pas été appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)