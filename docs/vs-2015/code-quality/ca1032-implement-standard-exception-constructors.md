---
title: 'CA1032 : implémenter des constructeurs d’exception standard | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b471387db3ce52944ffad3841dc7e946c4d44873
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661875"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032 : Implémenter des constructeurs d'exception standard
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type étend <xref:System.Exception?displayProperty=fullName> et ne déclare pas tous les constructeurs requis.

## <a name="rule-description"></a>Description de la règle
 Les types d’exceptions doivent implémenter les constructeurs suivants :

- public NewException ()

- public NewException (String)

- public NewException (String, exception)

- NewException protected ou Private (SerializationInfo, StreamingContext)

  Ne pas fournir le jeu complet de constructeurs peut rendre difficile une gestion des exceptions correcte. Par exemple, le constructeur qui a la signature `NewException(string, Exception)` est utilisé pour créer des exceptions provoquées par d’autres exceptions. Sans ce constructeur, vous ne pouvez pas créer et lever une instance de votre exception personnalisée qui contient une exception interne (imbriquée), ce que le code managé doit faire dans une telle situation. Les trois premiers constructeurs d’exception sont publics par Convention. Le quatrième constructeur est protégé dans les classes non scellées et privé dans les classes sealed. Pour plus d’informations, consultez [CA2229 : implémenter des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez les constructeurs manquants à l’exception et assurez-vous qu’ils ont l’accessibilité correcte.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle lorsque la violation est provoquée par l’utilisation d’un niveau d’accès différent pour les constructeurs publics.

## <a name="example"></a>Exemple
 L’exemple suivant contient un type d’exception qui enfreint cette règle et un type d’exception qui est correctement implémenté.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]
