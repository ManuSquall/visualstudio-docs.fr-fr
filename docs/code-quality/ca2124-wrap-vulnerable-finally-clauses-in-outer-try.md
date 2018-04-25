---
title: 'CA2124 : Incluez dans un wrapper les clauses finally vulnérables dans un bloc try externe'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d46bc7bcfa8c1918091fabbbd759172259ea9ba6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="ca2124-wrap-vulnerable-finally-clauses-in-outer-try"></a>CA2124 : Incluez dans un wrapper les clauses finally vulnérables dans un bloc try externe
|||
|-|-|
|TypeName|WrapVulnerableFinallyClausesInOuterTry|
|CheckId|CA2124|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Dans les versions 1.0 et 1.1 de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], une méthode publique ou protégée contient un `try` / `catch` / `finally` bloc. Le `finally` bloc semble réinitialiser l’état de sécurité et n’est pas placé dans un `finally` bloc.

## <a name="rule-description"></a>Description de la règle
 Cette règle recherche `try` / `finally` blocs dans le code qui cible des versions 1.0 et 1.1 de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] qui peuvent être vulnérables aux filtres d’exception malveillants présents dans la pile des appels. Si des opérations sensibles telles que l’emprunt d’identité se produisent dans le bloc try, et une exception est levée, le filtre peut s’exécuter avant le `finally` bloc. Pour l’exemple d’emprunt d’identité, cela signifie que le filtre s’exécute en tant que l’utilisateur représenté. Les filtres sont actuellement uniquement applicables en Visual Basic.

> [!WARNING]
>  **Remarque** dans les versions 2.0 et ultérieures de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], le runtime protège automatiquement un `try` / `catch` /  `finally` empêcher des filtres d’exception malveillants, si la réinitialisation se produit directement dans la méthode qui contient le bloc d’exception.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Placez le désencapsulée `try` / `finally` dans un bloc try externe. Consultez le deuxième exemple qui suit. Cela force le `finally` à exécuter avant le code de filtre.

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
 Le pseudo-code suivant illustre le modèle que vous pouvez utiliser pour protéger votre code et satisfaire cette règle.

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