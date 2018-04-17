---
title: 'CA2106 : Sécuriser les assertions | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2b49ab6d6cd99dc2865be21a2ed68579922bbb1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2106-secure-asserts"></a>CA2106 : Assertions sécurisées
|||  
|-|-|  
|TypeName|SecureAsserts|  
|CheckId|CA2106|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Une méthode déclare une autorisation et aucune vérification de sécurité n’est exécutée sur l’appelant.  
  
## <a name="rule-description"></a>Description de la règle  
 L'assertion d'une autorisation de sécurité effectuée sans vérification de sécurité peut rendre votre code vulnérable et facile à exploiter. Un parcours de pile de sécurité s’arrête lorsqu’une autorisation de sécurité est déclarée. Si vous déclarez une autorisation sans effectuer aucune vérification sur l’appelant, l’appelant indirectement exécuter du code à l’aide de vos autorisations. Assertions sans contrôles de sécurité sont autorisées uniquement lorsque vous êtes sûr que l’assertion ne peut pas être utilisée de manière nuisible. Une assertion est sans incidence si le code que vous appelez ne présente aucun danger ou si les utilisateurs ne peut pas transmettre des informations arbitraires au code que vous appelez.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez une demande de sécurité à la méthode ou son type déclarant.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle uniquement après un examen minutieux de la sécurité.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>   
 [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)