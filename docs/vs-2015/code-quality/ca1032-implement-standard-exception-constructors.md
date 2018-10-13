---
title: 'CA1032 : Implémenter des constructeurs d’exception standard | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1032
- ImplementStandardExceptionConstructors
helpviewer_keywords:
- CA1032
- ImplementStandardExceptionConstructors
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 871381e1013face4531e90b06d680d194955e3c0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193594"
---
# <a name="ca1032-implement-standard-exception-constructors"></a>CA1032 : Implémenter des constructeurs d'exception standard
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|ImplementStandardExceptionConstructors|
|CheckId|CA1032|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type étend <xref:System.Exception?displayProperty=fullName> et ne déclare pas tous les constructeurs requis.

## <a name="rule-description"></a>Description de la règle
 Types d’exception doivent implémenter les constructeurs suivants :

-   NewException() public

-   NewException(string) public

-   publique NewException (string, Exception)

-   protégé ou privée NewException (SerializationInfo, StreamingContext)

 Ne pas fournir le jeu complet de constructeurs peut rendre difficile une gestion des exceptions correcte. Par exemple, le constructeur qui a la signature `NewException(string, Exception)` est utilisé pour créer des exceptions provoquées par d’autres exceptions. Sans ce constructeur, vous ne pouvez pas créer et levez une instance de votre exception personnalisée qui contient une exception interne (imbriquée), qui est le code managé doit faire dans une telle situation. Les premiers constructeurs de trois exception sont publics par convention. Le quatrième constructeur est protégé dans les classes non scellés et privées dans les classes sealed. Pour plus d’informations, consultez [CA2229 : implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md)

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez les constructeurs manquants à l’exception et assurez-vous qu’ils ont l’accessibilité appropriée.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle quand la violation est due à l’aide d’un niveau d’accès différent pour les constructeurs publics.

## <a name="example"></a>Exemple
 L’exemple suivant contient un type d’exception qui enfreint cette règle et un type d’exception qui est implémenté correctement.

 [!code-csharp[FxCop.Design.ExceptionMultipleCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionMultipleCtors/cs/FxCop.Design.ExceptionMultipleCtors.cs#1)]



