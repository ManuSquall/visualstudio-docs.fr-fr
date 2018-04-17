---
title: 'CA2202 : Ne pas supprimer des objets plusieurs fois | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.openlocfilehash: e8d7132f9f4ac935b49ad61a7b3e4df307395e73
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202 : Ne pas supprimer des objets plusieurs fois
|||  
|-|-|  
|TypeName|DoNotDisposeObjectsMultipleTimes|  
|CheckId|CA2202|  
|Category|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Une implémentation de méthode contient des chemins d’accès de code qui peuvent provoquer des appels multiples à <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> ou un Dispose équivalent, tel qu’une méthode Close() sur certains types sur le même objet.  
  
## <a name="rule-description"></a>Description de la règle  
 A implémenté correctement <xref:System.IDisposable.Dispose%2A> méthode peut être appelée plusieurs fois sans lever d’exception. Toutefois, cela n’est pas garanti et pour éviter de générer un <xref:System.ObjectDisposedException?displayProperty=fullName> vous ne devez pas appeler <xref:System.IDisposable.Dispose%2A> plusieurs fois sur un objet.  
  
## <a name="related-rules"></a>Règles associées  
 [CA2000 : Supprimez les objets avant de perdre l’étendue](../code-quality/ca2000-dispose-objects-before-losing-scope.md)  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez l’implémentation donc autrement indépendamment du chemin de code <xref:System.IDisposable.Dispose%2A> est appelée qu’une seule fois pour l’objet.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. Même si <xref:System.IDisposable.Dispose%2A> pour l’objet est connu pour être en toute sécurité peut être appelée plusieurs fois, l’implémentation peut changer à l’avenir.  
  
## <a name="example"></a>Exemple  
 Imbriqué `using` instructions (`Using` en Visual Basic) peuvent provoquer des violations de l’avertissement CA2202. Si la ressource IDisposable d’interne imbriquée `using` instruction contient la ressource d’externe `using` instruction, le `Dispose` méthode de la ressource imbriquée libère la ressource contenue. Lorsque cette situation se produit, le `Dispose` méthode externe `using` instruction essaie de supprimer sa ressource pour la deuxième fois.  
  
 Dans l’exemple suivant, un <xref:System.IO.Stream> objet qui est créé en externe à l’aide d’instruction est libérée à la fin de l’instruction using interne dans la méthode Dispose de la <xref:System.IO.StreamWriter> objet qui contient le `stream` objet. À la fin de l’élément externe `using` instruction, le `stream` objet est libéré une deuxième fois. La deuxième version est une violation de CA2202.  
  
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
 Pour résoudre ce problème, utilisez un `try` / `finally` bloc au lieu d’externe `using` instruction. Dans le `finally` bloquer, assurez-vous que le `stream` ressource n’est pas null.  
  
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
 <xref:System.IDisposable?displayProperty=fullName>   
 [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)