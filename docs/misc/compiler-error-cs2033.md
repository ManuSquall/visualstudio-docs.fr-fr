---
title: "Erreur du compilateur CS2033 | Microsoft Docs"
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
  - "CS2033"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2033"
ms.assetid: edb5784a-5195-4f72-b73d-d1ec9ed3766e
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS2033
Impossible de créer le nom de fichier court 'filename' quand un nom de fichier long avec le même nom de fichier court existe déjà  
  
 Compilez tous les fichiers C\# portant un nom de plus de huit caractères. Ensuite, compilez un autre fichier avec la version courte du nom de fichier précédent \(par exemple les six premiers caractères du nom plus « ~1 »\). La deuxième compilation générera cette erreur.  
  
 Pour résoudre cette erreur, renommez le nom de fichier court en utilisant un nom qui n’entre pas en conflit avec le nom de fichier long.