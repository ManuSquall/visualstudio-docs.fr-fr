---
title: "Chiffre hexad&#233;cimal attendu | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1023"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Chiffre hexad&#233;cimal attendu
Vous avez créé une séquence d'échappement Unicode incorrecte.  Les séquences d'échappement Unicode commencent par \\u, suivi d'exactement quatre chiffres hexadécimaux \(ni plus, ni moins\).  Les chiffres hexadécimaux Unicode peuvent contenir uniquement les nombres de 0 à 9, les lettres majuscules de A à F et les lettres minuscules de a à f.  L'exemple suivant montre une séquence d'échappement Unicode correctement formée.  
  
```javascript  
z = "\u1A5F";  
```  
  
### Pour corriger cette erreur  
  
-   Assurez\-vous que les chiffres hexadécimaux Unicode commencent par \\u, qu'ils contiennent uniquement les nombres de 0 à 9, les lettres majuscules de A à F, les lettres minuscules de a à f et qu'ils sont regroupés en séquences de quatre chiffres.  
  
    > [!NOTE]
    >  Si vous souhaitez utiliser le texte littéral \\u dans une chaîne, utilisez deux barres obliques inverses \(\\\\u\) pour placer la première barre oblique inverse dans une séquence d'échappement.  
  
## Voir aussi  
 [Types de données](../../javascript/data-types-javascript.md)