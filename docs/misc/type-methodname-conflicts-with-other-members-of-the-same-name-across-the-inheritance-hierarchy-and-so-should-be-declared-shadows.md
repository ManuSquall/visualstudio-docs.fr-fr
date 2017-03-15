---
title: "&lt;type&gt; &#39;&lt;nom_m&#233;thode&gt;&#39; est en conflit avec d’autres membres du m&#234;me nom dans la hi&#233;rarchie d’h&#233;ritage et doit &#234;tre d&#233;clar&#233; &#39;Shadows&#39; | Microsoft Docs"
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
  - "vbc42000"
  - "bc42000"
helpviewer_keywords: 
  - "BC42000"
ms.assetid: 3081635f-99a9-4e90-997f-82251144d80f
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type&gt; &#39;&lt;nom_m&#233;thode&gt;&#39; est en conflit avec d’autres membres du m&#234;me nom dans la hi&#233;rarchie d’h&#233;ritage et doit &#234;tre d&#233;clar&#233; &#39;Shadows&#39;
Une interface qui hérite de deux ou plusieurs interfaces définit une procédure portant le même nom qu’une procédure déjà définie dans plusieurs interfaces de base. La procédure dans cette interface doit occulter l’une des procédures de l’interface de base.  
  
 Ce message est un avertissement.`Shadows` est supposé par défaut. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42000  
  
### Pour corriger cette erreur  
  
-   Si vous prévoyez de masquer l’une des procédures de l’interface de base, ajoutez le mot clé `Shadows` à la nouvelle déclaration de procédure.  
  
-   Si vous ne prévoyez pas de masquer les procédures de l’interface de base, modifiez le nom de la nouvelle procédure.  
  
## Voir aussi  
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Shadowing in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)