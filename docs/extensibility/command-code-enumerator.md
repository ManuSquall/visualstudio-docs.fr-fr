---
title: "&#201;num&#233;rateur de Code de commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "énumérateur de code de commande"
  - "contrôle plug-ins de source, énumération de code de commande"
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# &#201;num&#233;rateur de Code de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cet énumérateur est utilisé dans les options de la [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) et [SccPopulateList](../extensibility/sccpopulatelist-function.md)pour indiquer la commande pour laquelle les options sont spécifiées.  
  
## Syntaxe  
  
```  
enum SCCCOMMAND {  
   SCC_COMMAND_GET,  
   SCC_COMMAND_CHECKOUT,  
   SCC_COMMAND_CHECKIN,  
   SCC_COMMAND_UNCHECKOUT,  
   SCC_COMMAND_ADD,  
   SCC_COMMAND_REMOVE,  
   SCC_COMMAND_DIFF,  
   SCC_COMMAND_HISTORY,  
   SCC_COMMAND_RENAME,  
   SCC_COMMAND_PROPERTIES,  
   SCC_COMMAND_OPTIONS  
};  
```  
  
## Membres  
 SCC\_COMMAND\_GET  
 Correspond à la [SccGet](../extensibility/sccget-function.md).  
  
 SCC\_COMMAND\_CHECKOUT  
 Correspond à la [SccCheckout](../extensibility/scccheckout-function.md).  
  
 SCC\_COMMAND\_CHECKIN  
 Correspond à la [SccCheckin](../extensibility/scccheckin-function.md).  
  
 SCC\_COMMAND\_UNCHECKOUT  
 Correspond à la [SccUncheckout](../extensibility/sccuncheckout-function.md).  
  
 SCC\_COMMAND\_ADD  
 Correspond à la [SccAdd](../extensibility/sccadd-function.md).  
  
 SCC\_COMMAND\_REMOVE  
 Correspond à la [SccRemove](../extensibility/sccremove-function.md).  
  
 SCC\_COMMAND\_DIFF  
 Correspond à la [SccDiff](../extensibility/sccdiff-function.md).  
  
 SCC\_COMMAND\_HISTORY  
 Correspond à la [SccHistory](../extensibility/scchistory-function.md).  
  
 SCC\_COMMAND\_RENAME  
 Correspond à la [SccRename](../extensibility/sccrename-function.md).  
  
 SCC\_COMMAND\_PROPERTIES  
 Correspond à la [SccProperties](../extensibility/sccproperties-function.md).  
  
 SCC\_COMMAND\_OPTIONS  
 Correspond à la [SccSetOption](../extensibility/sccsetoption-function.md).  
  
## Voir aussi  
 [Plug\-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)