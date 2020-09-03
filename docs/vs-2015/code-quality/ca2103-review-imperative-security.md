---
title: 'Ca2103 : Vérifiez la sécurité impérative | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ade0d10e203752c7412929c6f5f44d9cbfaacfa6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521262"
---
# <a name="ca2103-review-imperative-security"></a>CA2103 : Vérifiez la sécurité impérative
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|Category|Microsoft.Security|
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
 [Données et modélisation des instructions de](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [codage sécurisé](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
