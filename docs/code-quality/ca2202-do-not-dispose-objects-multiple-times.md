---
title: "CA2202 : Ne pas supprimer d'objets plusieurs fois"
ms.date: 07/16/2019
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c7fa7756383426f990e18225995a768de9fefbd
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231738"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202 : Ne pas supprimer d'objets plusieurs fois

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une implémentation de méthode contient des chemins d’accès de code qui <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> peuvent provoquer des appels multiples vers ou un équivalent dispose, comme une méthode Close () sur certains types, sur le même objet.

## <a name="rule-description"></a>Description de la règle

Une méthode correctement <xref:System.IDisposable.Dispose%2A> implémentée peut être appelée plusieurs fois sans lever d’exception. Toutefois, cela n’est pas garanti et, pour éviter <xref:System.ObjectDisposedException?displayProperty=fullName> de générer un, <xref:System.IDisposable.Dispose%2A> vous ne devez pas appeler plus d’une fois sur un objet.

## <a name="related-rules"></a>Règles associées

- [CA2000 Supprimer les objets avant la perte de portée](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, modifiez l’implémentation afin que, quel que soit le chemin <xref:System.IDisposable.Dispose%2A> d’accès du code, soit appelée une seule fois pour l’objet.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle. Même si <xref:System.IDisposable.Dispose%2A> pour l’objet est connu pour être appelé plusieurs fois en toute sécurité, l’implémentation peut changer à l’avenir.

## <a name="example"></a>Exemple

Les instructions imbriquées`Using` (dans Visual Basic) peuvent provoquer des violations de l’avertissement CA2202. `using` Si la ressource IDisposable de l’instruction interne `using` imbriquée contient la ressource de l’instruction externe `using` , la `Dispose` méthode de la ressource imbriquée libère la ressource contenue. Lorsque cette situation se produit, `Dispose` la méthode de l' `using` instruction externe tente de supprimer sa ressource pour la deuxième fois.

Dans l’exemple suivant, un <xref:System.IO.Stream> objet créé dans une instruction using externe est libéré à la fin de l’instruction using interne de la méthode dispose de l' <xref:System.IO.StreamWriter> objet qui contient l' `stream` objet. À la fin de l’instruction `using` externe, l' `stream` objet est libéré une deuxième fois. La deuxième version est une violation de CA2202.

```csharp
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>Exemple

Pour résoudre ce problème, utilisez un `try` / `finally` bloc à la place de `using` l’instruction externe. Dans le `finally` bloc, assurez-vous `stream` que la ressource n’a pas la valeur null.

```csharp
Stream stream = null;
try
{
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);
    using (StreamWriter writer = new StreamWriter(stream))
    {
        stream = null;
        // Use the writer object...
    }
}
finally
{
    stream?.Dispose();
}
```

> [!TIP]
> La `?.` syntaxe ci-dessus est l' [opérateur conditionnel null](/dotnet/csharp/language-reference/operators/member-access-operators#null-conditional-operators--and-).

## <a name="see-also"></a>Voir aussi

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)