---
title: 'Ca2219 : ne levez pas d’exceptions dans les clauses d’exception | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 960c74625a04b209dc9aa251256e994517a3a52f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538526"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219 : Ne pas lever d'exceptions dans les clauses d'exception
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture, rupture|

## <a name="cause"></a>Cause :
 Une exception est levée à partir d’une `finally` clause, d’un filtre ou d’une clause Fault.

## <a name="rule-description"></a>Description de la règle
 Quand une exception est levée dans une clause d’exception, cela augmente considérablement la difficulté du débogage.

 Quand une exception est levée dans une `finally` clause or, la nouvelle exception masque l’exception active, le cas échéant. Cela rend l’erreur d’origine difficile à détecter et à déboguer.

 Quand une exception est levée dans une clause de filtre, le Runtime intercepte l’exception en mode silencieux et fait en sorte que le filtre ait la valeur false. Il n’existe aucun moyen de déterminer la différence entre le filtre évalué à false et une exception levée à partir d’un filtre. Cela complique la détection et le débogage des erreurs dans la logique du filtre.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger cette violation de cette règle, ne levez pas explicitement d’exception à partir d’une `finally` clause, d’un filtre ou d’une clause Fault.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement pour cette règle. Il n’existe aucun scénario dans lequel une exception levée dans une clause d’exception offre un avantage au code en cours d’exécution.

## <a name="related-rules"></a>Règles associées
 [CA1065 : Ne pas lever d'exceptions dans les emplacements inattendus](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Voir aussi
 [Avertissements de conception](../code-quality/design-warnings.md)
