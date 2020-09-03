---
title: 'CA1064 : les exceptions doivent être publiques | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1064
- ExceptionsShouldBePublic
helpviewer_keywords:
- ExceptionsShouldBePublic
- CA1064
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fc78c4eaacc3ef0a480b913d20537aeebe5bfc01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539267"
---
# <a name="ca1064-exceptions-should-be-public"></a>CA1064 : Les exceptions doivent être publiques
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|ExceptionsShouldBePublic|
|CheckId|CA1064|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Une exception non publique dérive directement de <xref:System.Exception> , <xref:System.SystemException> ou <xref:System.ApplicationException> .

## <a name="rule-description"></a>Description de la règle
 Une exception interne est visible uniquement à l’intérieur de sa propre portée interne. Lorsque l'exception se situe en dehors de la portée interne, seule l'exception de base peut être utilisée pour intercepter l'exception. Si l’exception interne est héritée de <xref:System.Exception> , <xref:System.SystemException> ou <xref:System.ApplicationException> , le code externe ne disposera pas d’informations suffisantes pour savoir ce qu’il faut faire avec l’exception.

 Toutefois, si le code a une exception publique qui est utilisée par la suite comme base pour une exception interne, il est raisonnable de supposer que le code plus éloigné pourra faire une opération intelligente avec l’exception de base. L’exception publique contient plus d’informations que celles fournies par la fonction T :System.Exception, T:System.SystemException ou T :System.ApplicationException.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Rendez l’exception publique ou dérivez l’exception interne d’une exception publique qui n’est pas <xref:System.Exception> , <xref:System.SystemException> ou <xref:System.ApplicationException> .

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un message de cette règle si vous êtes sûr, dans tous les cas, que l’exception privée sera interceptée dans sa propre étendue interne.

## <a name="example"></a>Exemple
 Cette règle se déclenche sur la première méthode d’exemple, FirstCustomException, car la classe d’exception dérive directement de exception et est interne. La règle ne se déclenche pas sur la classe SecondCustomException, car bien que la classe dérive également directement d’exception, la classe est déclarée comme publique. La troisième classe ne déclenche pas non plus la règle, car elle ne dérive pas directement de <xref:System.Exception?displayProperty=fullName> , <xref:System.SystemException?displayProperty=fullName> ou <xref:System.ApplicationException?displayProperty=fullName> .

 [!code-csharp[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.design.exceptionsshouldbepublic.ca1064/cs/ca1064 - exceptionsshouldbepublic.cs#1)]
