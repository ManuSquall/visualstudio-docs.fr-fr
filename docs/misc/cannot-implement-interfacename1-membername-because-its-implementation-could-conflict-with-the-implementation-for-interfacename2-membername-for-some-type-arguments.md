---
title: "Impossible d’impl&#233;menter &#39;&lt;nom_interface1&gt;. &lt;nom_membre&gt;&#39;, car son impl&#233;mentation pourrait &#234;tre en conflit avec l’impl&#233;mentation de &#39;&lt;nom_interface2&gt;. &lt;nom_membre&gt;&#39;, pour certains arguments de type. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32125"
  - "vbc32125"
helpviewer_keywords: 
  - "BC32125"
ms.assetid: 74321d27-4ff8-440c-b5de-d67e98fff274
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’impl&#233;menter &#39;&lt;nom_interface1&gt;. &lt;nom_membre&gt;&#39;, car son impl&#233;mentation pourrait &#234;tre en conflit avec l’impl&#233;mentation de &#39;&lt;nom_interface2&gt;. &lt;nom_membre&gt;&#39;, pour certains arguments de type.
Une classe implémente plusieurs interfaces génériques, dont une hérite d’une autre, et deux implémentations d’un membre d’interface peuvent être en conflit pour certaines valeurs d’arguments de type.  
  
 Les instructions suivantes peuvent générer cette erreur.  
  
```  
Public Interface iFace1(Of t) Sub testSub() End Interface Public Interface iFace2(Of u) Inherits iFace1(Of u) End Interface Public Class testClass(Of y, z) Implements iFace1(Of y), iFace2(Of z) Public Sub testSuby() Implements iFace1(Of y).testSub End Sub Public Sub testSubz() Implements iFace1(Of z).testSub End Sub End Class  
```  
  
 Étant donné que `iFace2` hérite de `iFace1` à l’aide de son propre paramètre de type \(`u`\), `testClass` implémente deux versions de `iFace1.testSub` avec des signatures identiques si le même argument de type est transmis à `y` et `z`. Cela produit une ambiguïté à propos de la version à laquelle il faut accéder.  
  
 **ID d’erreur :** BC32125  
  
### Pour corriger cette erreur  
  
-   Modifiez la structure d’héritage des interfaces pour que `iFace1` ne puisse pas être implémentée avec deux arguments de type différents.  
  
     ou  
  
-   Supprimez de l’instruction `Implements` l’une des interfaces provoquant le conflit d’implémentation.  
  
## Voir aussi  
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)   
 [Interface Statement](/dotnet/visual-basic/language-reference/statements/interface-statement)   
 [Implements Statement](/dotnet/visual-basic/language-reference/statements/implements-statement)   
 [NOT IN BUILD : Implements \(mot clé\) et Implements \(instruction\)](http://msdn.microsoft.com/fr-fr/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)