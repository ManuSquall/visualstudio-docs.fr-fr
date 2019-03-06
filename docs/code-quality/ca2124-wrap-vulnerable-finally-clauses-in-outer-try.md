---
title: 'CA2124 : Incluez dans un wrapper les clauses finally vulnérables dans un bloc try externe'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
helpviewer_keywords:
- CA2124
- WrapVulnerableFinallyClausesInOuterTry
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c35a15e9ce1468edd2882396192a27a3fcc2c86
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970346"
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124 : Incluez dans un wrapper les clauses finally vulnérables dans un bloc try externe

|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Dans les versions 1.0 et 1.1 du .NET Framework, une méthode publique ou protégée contient un `try` / `catch` / `finally` bloc. Le `finally` bloc semble réinitialiser l’état de sécurité et n’est pas placé dans un `finally` bloc.

## <a name="rule-description"></a>Description de la règle
 Cette règle localise `try` / `finally` blocs dans le code qui cible les versions 1.0 et 1.1 du .NET Framework qui peuvent être vulnérables aux filtres d’exception malveillants présents dans la pile des appels. Si des opérations sensibles telles que l’emprunt d’identité se produisent dans le bloc try, et une exception est levée, le filtre peut s’exécuter avant le `finally` bloc. Pour l’exemple d’emprunt d’identité, cela signifie que le filtre s’exécuterait comme l’utilisateur avec emprunt d’identité. Les filtres sont actuellement uniquement applicables en Visual Basic.

> [!NOTE]
> Dans les versions 2.0 et ultérieures du .NET Framework, le runtime protège automatiquement un `try` / `catch` /  `finally` empêcher des filtres d’exception malveillants, si la réinitialisation se produit directement dans la méthode qui contient le bloc d’exception.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Placez le texte désencapsulé `try` / `finally` dans un bloc try externe. Consultez le deuxième exemple qui suit. Cela force le `finally` s’exécute avant le code de filtre.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="pseudo-code-example"></a>Exemple de pseudo-code

### <a name="description"></a>Description

Le pseudo-code suivant illustre le modèle détecté par cette règle.

```csharp
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

Le pseudo-code suivant illustre le modèle que vous pouvez utiliser pour protéger votre code et satisfaire cette règle.

```csharp
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