---
title: "&#39;)&#39; attendu dans l&#39;expression r&#233;guli&#232;re (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5020"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# &#39;)&#39; attendu dans l&#39;expression r&#233;guli&#232;re (JavaScript)
Vous avez tenté de créer une capture d'expression régulière, une assertion ou un groupe sans inclure la parenthèse fermante.  Les parenthèses ont plusieurs utilités dans les expressions régulières.  Tout d'abord, elles sont utilisées pour capturer des sous\-expressions, spécifier des assertions ou regrouper des modèles afin que les éléments puissent être traités comme une seule unité par \*, \+, ?, etc.  
  
### Pour corriger cette erreur  
  
-   Ajoutez la parenthèse fermante la plus à droite.  
  
    > [!NOTE]
    >  Si vous souhaitez utiliser une parenthèse unique, échappez\-la à l'aide d'une barre oblique inverse « \\\( » afin qu'elle ne soit pas interprétée comme un caractère spécial par [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Voir aussi  
 [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)