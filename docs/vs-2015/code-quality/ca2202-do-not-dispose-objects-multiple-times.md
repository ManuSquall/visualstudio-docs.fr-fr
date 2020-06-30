---
title: 'CA2202 : ne pas supprimer les objets plusieurs fois | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 31bf7fe33aa59c3a713d2da81ddbd11ed6899723
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546287"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202 : Ne pas supprimer d'objets plusieurs fois
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une implémentation de méthode contient des chemins d’accès de code qui peuvent provoquer des appels multiples vers <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> ou un équivalent dispose, comme une méthode Close () sur certains types, sur le même objet.

## <a name="rule-description"></a>Description de la règle
 Une méthode correctement implémentée <xref:System.IDisposable.Dispose%2A> peut être appelée plusieurs fois sans lever d’exception. Toutefois, cela n’est pas garanti et, pour éviter de générer un, <xref:System.ObjectDisposedException?displayProperty=fullName> vous ne devez pas appeler plus d’une <xref:System.IDisposable.Dispose%2A> fois sur un objet.

## <a name="related-rules"></a>Règles associées
 [CA2000 : Supprimer les objets avant la mise hors de portée](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez l’implémentation afin que, quel que soit le chemin d’accès du code, <xref:System.IDisposable.Dispose%2A> soit appelée une seule fois pour l’objet.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Même si <xref:System.IDisposable.Dispose%2A> pour l’objet est connu pour être appelé plusieurs fois en toute sécurité, l’implémentation peut changer à l’avenir.

## <a name="example"></a>Exemple
 `using`Les instructions imbriquées ( `Using` dans Visual Basic) peuvent provoquer des violations de l’avertissement CA2202. Si la ressource IDisposable de l’instruction interne imbriquée `using` contient la ressource de l' `using` instruction externe, la `Dispose` méthode de la ressource imbriquée libère la ressource contenue. Lorsque cette situation se produit, la `Dispose` méthode de l' `using` instruction externe tente de supprimer sa ressource pour la deuxième fois.

 Dans l’exemple suivant, un <xref:System.IO.Stream> objet créé dans une instruction using externe est libéré à la fin de l’instruction using interne de la méthode dispose de l' <xref:System.IO.StreamWriter> objet qui contient l' `stream` objet. À la fin de l' `using` instruction externe, l' `stream` objet est libéré une deuxième fois. La deuxième version est une violation de CA2202.

```
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>Exemple
 Pour résoudre ce problème, utilisez un `try` / `finally` bloc à la place de l' `using` instruction externe. Dans le bloc, assurez-vous `finally` que la `stream` ressource n’a pas la valeur null.

```
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
 <xref:System.IDisposable?displayProperty=fullName>[Modèle de suppression](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
