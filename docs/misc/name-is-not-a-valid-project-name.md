---
title: "&lt;name&gt; is not a valid project name. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VS_E_INVALIDPROJECTNAME"
  - "vs.message.0x800A00D2"
ms.assetid: 2e8f3e58-f5f0-4f12-bae9-3acc58c0dca6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &lt;name&gt; is not a valid project name.
Cette erreur se produit généralement lorsque la commande `File.NewProject` est émise à partir de la fenêtre **Commande** ou de la zone de texte **Rechercher\/Commande** et qu'un nom de projet incorrect a été spécifié dans *projectname*.  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que le nom de projet ne contient pas d'espaces superflus et qu'il ne s'agit pas d'un mot réservé, tel que NUL, CON ou AUX.  
  
     \- ou \-  
  
     Entrez à nouveau la commande sans spécifier le nom de projet.  
  
## Voir aussi  
 [Commande, fenêtre](../ide/reference/command-window.md)