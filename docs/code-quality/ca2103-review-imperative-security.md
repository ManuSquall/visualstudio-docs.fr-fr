---
title: 'CA2103 : Vérifiez la sécurité impérative | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f5a46629efacc37af593e4cd7487b69031cf6bb1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2103-review-imperative-security"></a>CA2103 : Vérifiez la sécurité impérative
|||  
|-|-|  
|TypeName|ReviewImperativeSecurity|  
|CheckId|CA2103|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Une méthode utilise la sécurité impérative et est susceptible de construire l'autorisation à l'aide d'informations d'état ou de valeurs de retour qui peuvent changer pendant que la demande est active.  
  
## <a name="rule-description"></a>Description de la règle  
 La sécurité impérative utilise des objets managés pour spécifier des autorisations et des actions de sécurité pendant l’exécution de code, par rapport à la sécurité déclarative qui utilise des attributs pour stocker des autorisations et des actions dans les métadonnées. La sécurité impérative est très flexible car vous pouvez définir l’état d’un objet d’autorisation et sélectionnez les actions de sécurité à l’aide des informations qui ne sont pas disponibles jusqu'à l’exécution. Avec qui flexibilité le risque que les informations d’exécution que vous utilisez pour déterminer que l’état d’une autorisation ne reste pas inchangées tant que l’action est en vigueur.  
  
 Utilisez la sécurité de déclaration dès que possible. Les demandes déclaratives sont plus faciles à comprendre.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Révisez les demandes de sécurité impérative pour vous assurer que l’état de l’autorisation ne repose pas sur les informations qui peuvent changer tant que l’autorisation est utilisée.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle si l’autorisation ne repose pas sur la modification de données. Toutefois, il est préférable de modifier la demande impérative en son équivalent déclaratif.  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)   
 [Données et modélisation](/dotnet/framework/data/index)