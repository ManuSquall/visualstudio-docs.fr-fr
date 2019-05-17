---
title: 'CA2103 : Vérifiez la sécurité impérative | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5b8b3067d5c8ab8204d6ad723315c400e7b27552
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694929"
---
# <a name="ca2103-review-imperative-security"></a>CA2103 : Vérifiez la sécurité impérative
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode utilise la sécurité impérative et est susceptible de construire l'autorisation à l'aide d'informations d'état ou de valeurs de retour qui peuvent changer pendant que la demande est active.

## <a name="rule-description"></a>Description de la règle
 Sécurité impérative utilise des objets managés pour spécifier des autorisations et des actions de sécurité pendant l’exécution de code, par rapport à la sécurité déclarative qui utilise des attributs pour stocker des autorisations et des actions dans les métadonnées. Sécurité impérative est très flexible, car vous pouvez définir l’état d’un objet d’autorisation et sélectionner des actions de sécurité à l’aide d’informations qui ne sont pas disponibles jusqu'à l’exécution. Avec qui flexibilité vient le risque que les informations de runtime qui vous permet de déterminer que l’état d’une autorisation ne reste pas inchangées tant que l’action est en vigueur.

 Utilisez la sécurité de déclaration dès que possible. Les demandes déclaratives sont plus faciles à comprendre.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Passez en revue les demandes de sécurité impératives pour vous assurer que l’état de l’autorisation ne repose pas sur les informations qui peuvent changer tant que l’autorisation est utilisée.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si l’autorisation ne repose pas sur la modification de données. Toutefois, il est préférable de modifier la demande impérative en son équivalent déclaratif.

## <a name="see-also"></a>Voir aussi
 [Instructions de codage sécurisé](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [données et modélisation](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
