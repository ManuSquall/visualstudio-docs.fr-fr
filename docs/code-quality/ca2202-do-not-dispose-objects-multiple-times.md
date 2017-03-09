---
title: "CA2202 : Ne pas supprimer des objets plusieurs fois | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2202"
  - "Do not dispose objects multiple times"
  - "DoNotDisposeObjectsMultipleTimes"
helpviewer_keywords: 
  - "CA2202"
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2202 : Ne pas supprimer des objets plusieurs fois
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDisposeObjectsMultipleTimes|  
|CheckId|CA2202|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une implémentation de méthode contient des chemins d'accès de code qui peuvent provoquer des appels multiples à <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> ou un équivalent Dispose \(par exemple, une méthode Close\(\) sur certains types sur le même objet\).  
  
## Description de la règle  
 Une méthode <xref:System.IDisposable.Dispose%2A> correctement implémentée peut être appelée plusieurs fois sans lever d'exception.  Toutefois, cela n'est pas garanti et pour éviter de générer <xref:System.ObjectDisposedException?displayProperty=fullName>, vous ne devez pas appeler <xref:System.IDisposable.Dispose%2A> plusieurs fois sur un objet.  
  
## Règles connexes  
 [CA2000 : Supprimez les objets avant d'être hors de portée](../code-quality/ca2000-dispose-objects-before-losing-scope.md)  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez l'implémentation afin que <xref:System.IDisposable.Dispose%2A> soit appelé une seule fois pour l'objet, quel que soit le chemin d'accès de code.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  Même si <xref:System.IDisposable.Dispose%2A> pour l'objet peut être appelé plusieurs fois sans risque, l'implémentation peut changer à l'avenir.  
  
## Exemple  
 Les instructions `using` imbriquées \(`Using` en Visual Basic\) peuvent provoquer des violations de l'avertissement CA2202.  Si la ressource IDisposable de l'instruction `using` interne imbriquée contient la ressource de l'instruction `using` externe, la méthode `Dispose` de la ressource imbriquée libère la ressource contenue.  Lorsque cette situation se produit, la méthode `Dispose` de l'instruction `using` externe essaie de supprimer sa ressource pour la deuxième fois.  
  
 Dans l'exemple suivant, un objet <xref:System.IO.Stream> créé dans une instruction using externe est libéré à la fin de l'instruction using interne dans la méthode Dispose de l'objet <xref:System.IO.StreamWriter> qui contient l'objet `stream`.  À la fin de l'instruction `using` externe, l'objet de `stream` est diffusé une deuxième fois.  La deuxième version finale est une violation de CA2202.  
  
```  
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))  
{  
    using (StreamWriter writer = new StreamWriter(stream))  
    {  
        // Use the writer object...  
    }  
}  
  
```  
  
## Exemple  
 Pour résoudre ce problème, utilisez un bloc `try`\/`finally` au lieu de l'instruction `using` externe.  Dans le bloc `finally`, assurez\-vous que la ressource `stream` n'est pas null.  
  
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
  
## Voir aussi  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Modèle de suppression](../Topic/Dispose%20Pattern.md)