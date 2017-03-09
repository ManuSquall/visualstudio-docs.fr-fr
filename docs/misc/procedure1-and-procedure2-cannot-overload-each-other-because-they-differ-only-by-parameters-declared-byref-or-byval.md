---
title: "&#39;&lt;proc&#233;dure1&gt;&#39; et &#39;&lt;proc&#233;dure2&gt;&#39; ne peuvent pas se surcharger mutuellement, car seuls les param&#232;tres d&#233;clar&#233;s &#39;ByRef&#39; ou &#39;ByVal&#39; les diff&#233;rencient. | Microsoft Docs"
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
  - "vbc42003"
  - "bc42003"
helpviewer_keywords: 
  - "BC42003"
ms.assetid: f058f1e0-64d2-4497-85fc-a58e16b0d805
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;proc&#233;dure1&gt;&#39; et &#39;&lt;proc&#233;dure2&gt;&#39; ne peuvent pas se surcharger mutuellement, car seuls les param&#232;tres d&#233;clar&#233;s &#39;ByRef&#39; ou &#39;ByVal&#39; les diff&#233;rencient.
'\<procédure1\>' et '\<procédure2\>' ne peuvent pas se surcharger mutuellement, car seuls les paramètres déclarés ByRef ou ByVal les différencient Shadows supposé.  
  
 Deux déclarations de procédure spécifient le même nom et la même liste d’arguments, et la seule différence réside dans les caractéristiques de `ByRef` ou `ByVal` pour un ou plusieurs arguments. Les versions surchargées d’une procédure doivent différer l’une de l’autre par le nombre, l’ordre ou les types de données des arguments.  
  
 Ce message est un avertissement.`Shadows` est supposé par défaut. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42003  
  
### Pour corriger cette erreur  
  
-   Si vous souhaitez créer un ensemble de versions surchargées d’une procédure, faites en sorte que le nombre, l’ordre ou les types de données des arguments soient différents dans chaque version. Par ailleurs, ajoutez le mot clé `Overloads` à chaque déclaration.  
  
-   Si vous ne souhaitez pas surcharger une procédure, changez le nom de la procédure dans l’une des déclarations.  
  
## Voir aussi  
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)