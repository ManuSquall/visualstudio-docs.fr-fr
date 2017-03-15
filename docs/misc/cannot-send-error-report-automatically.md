---
title: "impossible d’envoyer le rapport d’erreurs automatiquement | Microsoft Docs"
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
  - "bc2027"
  - "vbc2027"
helpviewer_keywords: 
  - "BC2027"
ms.assetid: 84ba8580-2234-46d1-b4a5-94b03f64c0c7
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# impossible d’envoyer le rapport d’erreurs automatiquement
impossible d’envoyer le rapport d’erreurs automatiquement. Visitez le site web 'http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039' pour configurer les paramètres d’envoi des rapports d’erreurs.  
  
 Vous avez spécifié l’option de compilateur `/errorreport:send`, mais l’ordinateur n’est pas configuré pour envoyer automatiquement des rapports d’erreurs. Aucune information ne sera envoyée à propos des erreurs internes dans le compilateur Visual Basic.  
  
 **ID d’erreur :** BC2027  
  
### Pour corriger cette erreur  
  
-   Supprimez l’option de compilateur `/errorreport:send` ou remplacez\-la par `/errorreport:queue`, `/errorreport:prompt` ou `/errorreport:none`.  
  
     — ou —  
  
-   Activez le rapport d’erreurs automatique en suivant les instructions sur le site web [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039](http://go.microsoft.com/fwlink/?LinkId=42039).  
  
## Voir aussi  
 [\/errorreport](/dotnet/visual-basic/reference/command-line-compiler/errorreport)   
 [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=42039](http://go.microsoft.com/fwlink/?LinkId=42039)