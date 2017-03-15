---
title: "Erreur RC2115 du compilateur de ressources | Microsoft Docs"
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
  - "RC2115"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2115"
ms.assetid: 1b90feb0-f1fb-4f3c-8a9a-c44f9f8dc366
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Erreur RC2115 du compilateur de ressources
chaîne de texte ou ordinal attendu dans le contrôle  
  
 Le champ *text* d’une instruction CONTROL dans l’instruction **DIALOG** doit être une chaîne de texte ou une référence d’ordinal au type de contrôle. S’il s’agit d’un ordinal, veillez à utiliser une instruction `#define` pour le contrôle.