---
title: "Unable to delete file &lt;name&gt;. The file may be in use by another application or marked read-only. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_DELETEFILEFAILED"
  - "vs.message.0x800A00A2"
ms.assetid: 5c425dca-1d28-47a8-a11c-6a890be10baf
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to delete file &lt;name&gt;. The file may be in use by another application or marked read-only.
Cette erreur se produit généralement lorsque la disposition de clavier sélectionnée pour être supprimée est en cours d'utilisation ou en lecture seule.  
  
### Pour corriger cette erreur  
  
1.  Si une autre application utilise le fichier spécifié, fermez cette application.  
  
     \- ou \-  
  
     Si le fichier est en lecture seule, enlevez l'attribut lecture seule.  Vous pouvez modifier l'attribut de lecture seule dans la boîte de dialogue Propriétés du fichier, disponible dans l'Explorateur de fichiers.  
  
## Voir aussi  
 [Identification et personnalisation des raccourcis clavier](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)