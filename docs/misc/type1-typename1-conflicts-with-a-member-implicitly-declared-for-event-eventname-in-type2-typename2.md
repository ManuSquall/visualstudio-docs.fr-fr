---
title: "&lt;type1&gt; &#39;&lt;nom_type1&gt;&#39; est en conflit avec un membre d&#233;clar&#233; implicitement pour &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; dans &lt;type2&gt; &#39;&lt;nom_type2&gt;&#39; | Microsoft Docs"
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
  - "vbc31061"
  - "bc31061"
helpviewer_keywords: 
  - "BC31061"
ms.assetid: de5b1121-8c8f-4aba-a3e7-1e3e60df0dc5
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type1&gt; &#39;&lt;nom_type1&gt;&#39; est en conflit avec un membre d&#233;clar&#233; implicitement pour &#39;&lt;nom_&#233;v&#233;nement&gt;&#39; dans &lt;type2&gt; &#39;&lt;nom_type2&gt;&#39;
Le nom d’un membre de type est en conflit avec le nom d’un membre implicitement créé pour un événement. Les événements créent implicitement plusieurs variables implicites. Par exemple, la déclaration `Event X` déclare implicitement les noms `XEventHandler`, `XEvent`, `add_X` et `remove_X`.  
  
 **ID d’erreur :** BC31061  
  
### Pour corriger cette erreur  
  
-   Renommez le membre déclaré explicitement pour supprimer le conflit de noms.  
  
## Voir aussi  
 [NotInBuild : Instructions de déclaration en Visual Basic](http://msdn.microsoft.com/fr-fr/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)   
 [Events](/dotnet/visual-basic/programming-guide/language-features/events/events)