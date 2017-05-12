---
title: "&#39;]&#39; attendu dans l&#39;expression r&#233;guli&#232;re (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5019"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# &#39;]&#39; attendu dans l&#39;expression r&#233;guli&#232;re (JavaScript)
Vous avez tenté de créer une classe de caractères pour une correspondance d'expression régulière, mais avez omis le crochet droit.  Vous pouvez assembler différentes combinaisons de caractères littéraux pour former des classes de caractères en les plaçant entre crochets.  Une classe de caractères correspond à n'importe quel caractère qu'elle contient.  Par exemple, \/\[abc\]\/correspond à n'importe laquelle des lettres « a », « b » ou « c ».  
  
### Pour corriger cette erreur  
  
-   Ajoutez le crochet droit à l'expression régulière.  
  
    > [!NOTE]
    >  Si vous souhaitez utiliser un crochet unique, échappez\-le à l'aide d'une barre oblique inverse « \\\[ » afin qu'il ne soit pas interprété comme un caractère spécial par [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Voir aussi  
 [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)