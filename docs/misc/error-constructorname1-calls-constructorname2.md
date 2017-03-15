---
title: "&lt;erreur&gt;&#160;: &#39;&lt;nom_constructeur1&gt;&#39; appelle &#39;&lt;nom_constructeur2&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30297"
  - "bc30297"
helpviewer_keywords: 
  - "BC30297"
ms.assetid: dfca67d7-f4d7-4451-a937-68f22b8527d5
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;erreur&gt;&#160;: &#39;&lt;nom_constructeur1&gt;&#39; appelle &#39;&lt;nom_constructeur2&gt;&#39;
Un appel de constructeur circulaire s’est produit. Un constructeur appelle `Me.New()` ou `MyClass.New()`. Vous avez peut\-être tenté d’appeler un constructeur surchargé avec une liste d’arguments différente.  
  
 **ID d’erreur :** BC30297  
  
### Pour corriger cette erreur  
  
-   Utilisez une liste d’arguments différente pour appeler un constructeur surchargé.  
  
-   Si aucune surcharge n’est accessible, supprimez l’appel à `Me.New()` ou `MyClass.New()`.  
  
## Voir aussi  
 [NOT IN BUILD : Utilisation des constructeurs et des destructeurs](http://msdn.microsoft.com/fr-fr/548eebe1-86c4-4377-b2f5-447cb8be3d90)