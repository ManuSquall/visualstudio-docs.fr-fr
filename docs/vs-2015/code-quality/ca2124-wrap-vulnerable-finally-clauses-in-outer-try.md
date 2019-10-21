---
title: 'CA2124 : inclure dans un wrapper les clauses finally vulnérables dans un bloc try externe | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7a2a296f5dd3680209c14849b5bd863c01e6351d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660248"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124 : Incluez dans un wrapper les clauses finally vulnérables dans un bloc try externe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Dans les versions 1,0 et 1,1 de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], une méthode publique ou protégée contient un `try` / `catch` / bloc `finally`. Le bloc `finally` semble réinitialiser l’état de sécurité et n’est pas placé dans un bloc `finally`.

## <a name="rule-description"></a>Description de la règle
 Cette règle localise `try` / blocs `finally` dans le code qui ciblent les versions 1,0 et 1,1 du [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] qui peuvent être vulnérables aux filtres d’exceptions malveillants présents dans la pile des appels. Si des opérations sensibles telles que l’emprunt d’identité se produisent dans le bloc try et qu’une exception est levée, le filtre peut s’exécuter avant le bloc `finally`. Pour l’exemple d’emprunt d’identité, cela signifie que le filtre s’exécute en tant qu’utilisateur avec emprunt d’identité. Les filtres peuvent actuellement être implémentés uniquement dans Visual Basic.

> [!WARNING]
> Dans les versions 2,0 et ultérieures de l' [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], le runtime protège automatiquement un `try` / `catch` /  bloc `finally` des filtres d’exception malveillants, si la réinitialisation se produit directement dans la méthode qui contient le bloc d’exception.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Placez le `try` non encapsulé / `finally` dans un bloc try externe. Consultez le deuxième exemple qui suit. Cela force le `finally` à s’exécuter avant le code de filtre.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="pseudo-code-example"></a>Exemple de pseudo-code

### <a name="description"></a>Description
 Le pseudo-code suivant illustre le modèle détecté par cette règle.

### <a name="code"></a>Code

```
try {
   // Do some work.
   Impersonator imp = new Impersonator("John Doe");
   imp.AddToCreditCardBalance(100);
}
finally {
   // Reset security state.
   imp.Revert();
}
```

## <a name="example"></a>Exemple
 Le pseudo-code suivant illustre le modèle que vous pouvez utiliser pour protéger votre code et satisfaire à cette règle.

```
try {
     try {
        // Do some work.
     }
     finally {
        // Reset security state.
     }
}
catch()
{
    throw;
}
```
