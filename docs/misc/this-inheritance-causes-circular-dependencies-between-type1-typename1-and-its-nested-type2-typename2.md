---
title: "Cet h&#233;ritage provoque des d&#233;pendances circulaires entre &lt;type1&gt; &#39;&lt;nom_type1&gt;&#39; et son &lt;type2&gt; &#39;&lt;nom_type2&gt;&#39; imbriqu&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30907"
  - "bc30907"
helpviewer_keywords: 
  - "BC30907"
ms.assetid: 17d4f938-5895-4d33-943e-8abf0ceacdc9
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cet h&#233;ritage provoque des d&#233;pendances circulaires entre &lt;type1&gt; &#39;&lt;nom_type1&gt;&#39; et son &lt;type2&gt; &#39;&lt;nom_type2&gt;&#39; imbriqu&#233;
Une structure d’héritage entraîne une dépendance circulaire entre les classes imbriquées, autrement dit, deux classes qui héritent l’une de l’autre.  
  
 Le code suivant peut générer cette erreur.  
  
```  
Public Class c1 Inherits c3.c4 Public Class c2 End Class End Class Public Class c3 Inherits c1.c2 Public Class c4 End Class End Class  
```  
  
 Dans le code précédent, la classe `c1` hérite de la classe `c4`, mais `c4` est imbriqué dans `c3`, qui hérite de `c2` qui est imbriqué dans `c1`.  
  
 **ID d’erreur :** BC30907  
  
### Pour corriger cette erreur  
  
-   Supprimez les dépendances circulaires de la structure d’héritage.  
  
## Voir aussi  
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)