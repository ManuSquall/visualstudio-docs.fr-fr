---
title: "Une r&#233;f&#233;rence &#224; un membre non partag&#233; requiert une r&#233;f&#233;rence d’objet | Microsoft Docs"
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
  - "bc30469"
  - "vbc30469"
helpviewer_keywords: 
  - "BC30469"
ms.assetid: af503e8b-2e1f-4f91-a07f-b1ddd73dd4a6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une r&#233;f&#233;rence &#224; un membre non partag&#233; requiert une r&#233;f&#233;rence d’objet
Vous avez fait référence à un membre non partagé dans votre code et n’avez pas pu fournir une référence d’objet. Vous ne pouvez pas utiliser le nom de la classe proprement dit pour qualifier un membre qui n’est pas partagé. L’instance doit d’abord être déclarée comme variable objet et ensuite être référencée par le nom de la variable.  
  
 **ID d’erreur :** BC30469  
  
### Pour corriger cette erreur  
  
1.  Déclarez l’instance comme variable objet.  
  
2.  Faites référence à l’instance par le nom de la variable.  
  
## Voir aussi  
 [NOT IN BUILD : Présentation des classes](http://msdn.microsoft.com/fr-fr/cc2355a2-cb98-4353-9440-736585aec46c)   
 [NOT IN BUILD : Membres partagés en Visual Basic](http://msdn.microsoft.com/fr-fr/dbc3783f-83a2-4225-995d-c2d6d025663d)   
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [NOTINBUILD : Résolution d’une référence quand plusieurs variables portent le même nom](http://msdn.microsoft.com/fr-fr/9601e39f-1911-44e1-ace5-3f6e090408b9)