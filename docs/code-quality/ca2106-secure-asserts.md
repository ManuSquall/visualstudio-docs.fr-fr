---
title: 'CA2106 : Assertions sécurisées'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d4495dcbe951edd3e7eaa3b6ff0d2432bc0a7751
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232874"
---
# <a name="ca2106-secure-asserts"></a>CA2106 : Assertions sécurisées

|||
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Une méthode déclare une autorisation et n’effectue aucune vérification de sécurité sur l’appelant.

## <a name="rule-description"></a>Description de la règle
L’assertion d’une autorisation de sécurité effectuée sans vérification de sécurité peut rendre votre code vulnérable et facile à exploiter. Un parcours de la pile de sécurité s’arrête lorsqu’une autorisation de sécurité est déclarée. Si vous déclarez une autorisation sans effectuer de vérification sur l’appelant, l’appelant peut exécuter indirectement du code à l’aide de vos autorisations. Les assertions sans contrôles de sécurité sont autorisées si vous êtes sûr que l’assertion ne peut pas être utilisée de manière nocive. Une assertion est sans incidence si le code que vous appelez est sans conséquence, ou si les utilisateurs ne peuvent pas passer d’informations arbitraires au code que vous appelez.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, ajoutez une demande de sécurité à la méthode ou à son type déclarant.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Supprimez un avertissement de cette règle uniquement après une révision minutieuse de la sécurité.

## <a name="see-also"></a>Voir aussi

- <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName>
- [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)