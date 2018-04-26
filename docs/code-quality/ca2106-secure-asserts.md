---
title: 'CA2106 : Assertions sécurisées'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5863f4d8ca4db47f7e537f0b1abc5eb280434c80
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
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
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)