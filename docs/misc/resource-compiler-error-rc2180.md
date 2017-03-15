---
title: "Erreur du compilateur de ressources RC2180 | Microsoft Docs"
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
  - "RC2180"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2180"
ms.assetid: 6d296138-7989-491e-a45b-6c3a4743116a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# Erreur du compilateur de ressources RC2180
impossible d'ouvrir le fichier temporaire  
  
 Le compilateur de ressources\/Visual C\+\+ n’a pas pu ouvrir un fichier temporaire. La cause probable est que vous n’avez pas d’autorisations d’accès en écriture sur le répertoire ou que le répertoire n’existe pas. Le compilateur de ressources\/Visual C\+\+ essaie d’utiliser ces fichiers dans le répertoire spécifié par la variable d’environnement **TMP** ou le répertoire actuel si aucun n’est spécifié.