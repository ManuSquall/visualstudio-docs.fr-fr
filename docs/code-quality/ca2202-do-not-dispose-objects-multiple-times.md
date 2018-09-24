---
title: 'CA2202 : Ne pas supprimer des objets plusieurs fois'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4e805cb76ebe4c216b456f65ea3264f8f25561cc
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45548606"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202 : Ne pas supprimer des objets plusieurs fois

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une implémentation de méthode contient des chemins de code qui pouvait entraîner plusieurs appels à <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> ou un Dispose équivalent, tel qu’une méthode Close() sur certains types sur le même objet.

## <a name="rule-description"></a>Description de la règle

A implémenté correctement <xref:System.IDisposable.Dispose%2A> méthode peut être appelée plusieurs fois sans lever d’exception. Toutefois, cela n’est pas garanti et pour éviter de générer un <xref:System.ObjectDisposedException?displayProperty=fullName> vous ne devez pas appeler <xref:System.IDisposable.Dispose%2A> plusieurs fois sur un objet.

## <a name="related-rules"></a>Règles associées

- [CA2000 : Supprimez les objets avant de perdre l’étendue](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, modifier l’implémentation donc autrement indépendamment du chemin d’accès du code, <xref:System.IDisposable.Dispose%2A> est appelée qu’une seule fois pour l’objet.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle. Même si <xref:System.IDisposable.Dispose%2A> pour l’objet est connu pour être appelé en toute sécurité plusieurs fois, l’implémentation peut changer à l’avenir.

## <a name="example"></a>Exemple

Imbriqué `using` instructions (`Using` en Visual Basic) peuvent provoquer des violations de l’avertissement CA2202. Si la ressource IDisposable d’imbriquée interne `using` instruction contient la ressource d’externe `using` instruction, le `Dispose` méthode de la ressource imbriquée libère la ressource de relation contenant-contenue. Lorsque cette situation se produit, le `Dispose` méthode externe `using` instruction essaie de supprimer sa ressource pour une deuxième fois.

Dans l’exemple suivant, un <xref:System.IO.Stream> objet qui est créé en externe à l’aide d’instruction est libéré à la fin de l’instruction using interne dans la méthode Dispose de la <xref:System.IO.StreamWriter> objet qui contient le `stream` objet. À la fin de la liste externe `using` instruction, le `stream` objet est libéré une deuxième fois. La deuxième version est une violation de CA2202.

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

Pour résoudre ce problème, utilisez un `try` / `finally` bloc au lieu d’externe `using` instruction. Dans le `finally` bloquer, assurez-vous que le `stream` ressource n’est pas null.

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
    if(stream != null)
        stream.Dispose();
}
```

## <a name="see-also"></a>Voir aussi

- <xref:System.IDisposable?displayProperty=fullName>
- [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)