---
title: "L&#39;encodage de l&#39;URI &#224; d&#233;coder n&#39;est pas valide | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5025"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 029e0790-ffd1-496d-8700-3b3dbac1b6fd
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# L&#39;encodage de l&#39;URI &#224; d&#233;coder n&#39;est pas valide
Vous avez tenté de décoder un identificateur URI \(Uniform Resource Identifier\) qui n'est pas correctement formé.  Les identificateurs URI doivent respecter une syntaxe spéciale ; la plupart des caractères non alphanumériques doivent être encodés avant de pouvoir être utilisés dans un URI.  Vous pouvez utiliser les méthodes `encodeURI` et `encodeURIComponent` pour créer un identificateur URI à partir d'une chaîne [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] normale.  
  
 Un identificateur URI complet comprend une séquence de composants et de séparateurs.  Sa forme générale est la suivante :  
  
```javascript  
<Scheme>:<first>/<second>;<third>?<fourth>  
```  
  
 Les termes figurant entre les symboles « \< » et « \> » représentent les composants. Les caractères « : », « \/ », « ; » et « ? » sont réservés et utilisés comme séparateurs.  
  
### Pour corriger cette erreur  
  
-   Vérifiez que les identificateurs URI que vous tentez de décoder sont valides.  Vous ne pouvez pas décoder des chaînes [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] normales, car elles peuvent contenir des caractères non valides.  
  
## Voir aussi  
 [Fonction decodeURI](../../javascript/reference/decodeuri-function-javascript.md)   
 [decodeURIComponent, fonction](../../javascript/reference/decodeuricomponent-function-javascript.md)