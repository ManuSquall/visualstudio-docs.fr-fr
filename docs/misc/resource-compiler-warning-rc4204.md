---
title: "Avertissement RC4204 du compilateur de ressources | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RC4204"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC4204"
ms.assetid: f9a83b3c-d696-4b38-9576-945d1f6d0063
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Avertissement RC4204 du compilateur de ressources
Caractère ASCII non équivalent au code de touche virtuelle  
  
 Vous avez utilisé un littéral de chaîne pour le code de touche virtuelle dans un accélérateur de type VIRTKEY.  
  
 Cet avertissement ne vous empêche pas de continuer, mais sachez que les touches accélérateur générées risquent de ne pas correspondre à la chaîne spécifiée. \(Les VIRTKEY utilisent des codes de touches différents des accélérateurs ASCII.\)  
  
 Les littéraux de chaîne sont valides, mais le seul moyen de vous assurer que vous obtiendrez l’accélérateur souhaité consiste à utiliser les valeurs **VK\_\*** `#define` dans WINDOWS.h.