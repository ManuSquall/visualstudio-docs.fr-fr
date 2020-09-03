---
title: 'CA2106 : assertions sécurisées | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2106
- SecureAsserts
helpviewer_keywords:
- CA2106
- SecureAsserts
ms.assetid: 91feb36e-6e2c-436c-8272-5aee31f77e98
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: eb0e097c2f13fa9d9279a5f3e9761a53cb6e4b1d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547743"
---
# <a name="ca2106-secure-asserts"></a>CA2106 : Assertions sécurisées
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|SecureAsserts|
|CheckId|CA2106|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode déclare une autorisation et aucune vérification de sécurité n’est exécutée sur l’appelant.

## <a name="rule-description"></a>Description de la règle
 L’assertion d’une autorisation de sécurité effectuée sans vérification de sécurité peut rendre votre code vulnérable et facile à exploiter. Un parcours de la pile de sécurité s’arrête lorsqu’une autorisation de sécurité est déclarée. Si vous déclarez une autorisation sans effectuer de vérification sur l’appelant, l’appelant peut exécuter indirectement du code à l’aide de vos autorisations. Les assertions sans contrôles de sécurité sont autorisées uniquement lorsque vous êtes sûr que l’assertion ne peut pas être utilisée de manière nocive. Une assertion est inoffensive si le code que vous appelez est sans conséquence, ou si les utilisateurs ne peuvent pas passer d’informations arbitraires au code que vous appelez.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez une demande de sécurité à la méthode ou à son type déclarant.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle uniquement après une révision minutieuse de la sécurité.

## <a name="see-also"></a>Voir aussi
 <xref:System.Security.CodeAccessPermission.Assert%2A?displayProperty=fullName> [Instructions de codage sécurisé](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177)
