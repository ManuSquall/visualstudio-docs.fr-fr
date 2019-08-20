---
title: 'CA2103 : Vérifiez la sécurité impérative'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7acbb9d0127dd2ddb6668e72db8fa88124ec2b3c
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921427"
---
# <a name="ca2103-review-imperative-security"></a>CA2103 : Vérifiez la sécurité impérative

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|Catégorie|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Une méthode utilise la sécurité impérative et est susceptible de construire l'autorisation à l'aide d'informations d'état ou de valeurs de retour qui peuvent changer pendant que la demande est active.

## <a name="rule-description"></a>Description de la règle
La sécurité impérative utilise des objets managés pour spécifier des autorisations et des actions de sécurité pendant l’exécution du code, par rapport à la sécurité déclarative, qui utilise des attributs pour stocker des autorisations et des actions dans les métadonnées. La sécurité impérative est très flexible, car vous pouvez définir l’état d’un objet d’autorisation et sélectionner des actions de sécurité à l’aide d’informations qui ne sont disponibles qu’au moment de l’exécution. Cette flexibilité présente le risque que les informations d’exécution que vous utilisez pour déterminer l’état d’une autorisation ne restent pas inchangées tant que l’action est en vigueur.

Utilisez la sécurité de déclaration dès que possible. Les demandes déclaratives sont plus faciles à comprendre.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Passez en revue les demandes de sécurité impératives pour vous assurer que l’état de l’autorisation ne repose pas sur des informations qui peuvent changer tant que l’autorisation est utilisée.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle si l’autorisation ne repose pas sur la modification des données. Toutefois, il est préférable de modifier la demande impérative en son équivalent déclaratif.

## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)
- [Données et modélisation](/dotnet/framework/data/index)