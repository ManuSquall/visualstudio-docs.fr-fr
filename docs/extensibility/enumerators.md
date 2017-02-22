---
title: "&#201;num&#233;rateurs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle plug-ins de source, les énumérateurs"
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# &#201;num&#233;rateurs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette section répertorie les types de données d'énumérateur dans l'API de plug\-in de contrôle Source qui doit reconnaître le plug\-in de contrôle de code source.  
  
## Dans cette section  
 [Code de commande](../extensibility/command-code-enumerator.md)  
 Énumère les options pour la [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) et [SccPopulateList](../extensibility/sccpopulatelist-function.md) fonctions.  
  
 [Message](../extensibility/message-enumerator.md)  
 Énumère les indicateurs utilisés pour le rappel d'impression, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Code d'état de fichier](../extensibility/file-status-code-enumerator.md)  
 Contient des valeurs de constantes nommées qui spécifient l'état d'un fichier sous contrôle de code source.  
  
 [Code d'état Active](../extensibility/directory-status-code-enumerator.md)  
 Contient des valeurs de constantes nommées qui spécifient l'état d'un répertoire sous contrôle de code source.  
  
## Rubriques connexes  
 [Création d'un contrôle de Source de plug\-in](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Définit le SDK de plug\-in de contrôle Source et décrit les ressources incluses.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Invite l'utilisateur pour les options avancées pour la commande donnée.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Examine la liste des fichiers pour leur état actuel. Utilise en outre, le `pfnPopulate` \(fonction\) pour notifier l'appelant quand un fichier ne respectent pas les critères pour le `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Décrit la fonction de rappel qui est utilisée par [SccOpenProject](../extensibility/sccopenproject-function.md) pour afficher les messages de contrôle de source de plug\-in via l'IDE.  
  
 [Plug\-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)  
 Fournit une liste complète de tous les éléments dans l'API de plug\-in de contrôle de Source.