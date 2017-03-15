---
title: "L’instruction appelle de mani&#232;re r&#233;cursive le &#39;AddHandler&#39; conteneur pour l’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; | Microsoft Docs"
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
  - "bc41998"
  - "vbc41998"
helpviewer_keywords: 
  - "BC41998"
ms.assetid: 4375b191-fbd9-4e93-b9bb-9159d533ddf6
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’instruction appelle de mani&#232;re r&#233;cursive le &#39;AddHandler&#39; conteneur pour l’&#233;v&#233;nement &#39;&lt;nom_&#233;v&#233;nement&gt;&#39;
Les instructions dans l’accesseur `AddHandler` d’une définition d’événement ne doivent pas faire référence à l’événement directement.  
  
 L’approche recommandée consiste à stocker la liste des gestionnaires de l’événement comme champ privé dans la classe, la structure ou le module qui a défini l’événement. Pour plus d’informations, consultez [How to: Declare Custom Events To Avoid Blocking](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md) et [How to: Declare Custom Events To Conserve Memory](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md).  
  
 **ID d’erreur :** BC41998  
  
### Pour corriger cette erreur  
  
-   Réécrivez la définition d’événement pour éviter la récursivité.  
  
## Voir aussi  
 [AddHandler \- delete](http://msdn.microsoft.com/fr-fr/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [Event Statement](/dotnet/visual-basic/language-reference/statements/event-statement)   
 [How to: Declare Custom Events To Avoid Blocking](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Avoid%20Blocking%20\(Visual%20Basic\).md)   
 [How to: Declare Custom Events To Conserve Memory](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md)