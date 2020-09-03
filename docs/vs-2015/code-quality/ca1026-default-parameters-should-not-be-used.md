---
title: 'Ca1026 : les paramètres par défaut ne doivent pas être utilisés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a63d6e788dd1722d0c593469b225a4f1aeb4738d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548440"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026 : Les paramètres par défaut ne doivent pas être utilisés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type visible de l’extérieur contient une méthode visible de l’extérieur qui utilise un paramètre par défaut.

## <a name="rule-description"></a>Description de la règle
 Les méthodes qui utilisent des paramètres par défaut sont autorisées sous le Common Language Specification (CLS); Toutefois, la spécification CLS permet aux compilateurs d’ignorer les valeurs assignées à ces paramètres. Le code écrit pour les compilateurs qui ignorent les valeurs de paramètres par défaut doit fournir explicitement des arguments pour chaque paramètre par défaut. Pour conserver le comportement que vous souhaitez dans les langages de programmation, les méthodes qui utilisent des paramètres par défaut doivent être remplacées par des surcharges de méthode qui fournissent les paramètres par défaut.

 Le compilateur ignore les valeurs des paramètres par défaut pour l’extension managée pour C++ lorsqu’il accède au code managé. Le compilateur Visual Basic prend en charge les méthodes qui ont des paramètres par défaut qui utilisent le mot clé [facultatif](https://msdn.microsoft.com/library/4571ce88-a539-4115-b230-54eb277c6aa7) .

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, remplacez la méthode qui utilise des paramètres par défaut par des surcharges de méthode qui fournissent les paramètres par défaut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui utilise des paramètres par défaut et les méthodes surchargées qui fournissent une fonctionnalité équivalente.

 [!code-vb[FxCop.Design.DefaultParameters#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DefaultParameters/vb/FxCop.Design.DefaultParameters.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1025 : Remplacer les arguments répétitifs par un tableau params](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>Voir aussi
 [Indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
