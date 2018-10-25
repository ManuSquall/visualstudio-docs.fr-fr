---
title: Énumérateur de Code de statut de répertoire | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a4ffdef238aaa628d0b72bcc945cf3dc1754fd8b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833965"
---
# <a name="directory-status-code-enumerator"></a>Énumérateur de code de statut de répertoire
Le `SccDirStatus` énumérateur contient des valeurs de constantes nommées qui spécifient l’état d’un répertoire dans le système de contrôle source. Cette énumération est utilisée par le [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Cela a été introduite dans la version 1.2 de l’API de plug-in de contrôle de Source.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## <a name="members"></a>Membres  
 SCC_DIRSTATUS_INVALID  
 État n’a pas pu être obtenu ; ne comptez pas sur celle-ci.  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 Répertoire n’est pas sous contrôle de code source.  
  
 SCC_DIRSTATUS_CONTROLLED  
 Répertoire est sous contrôle de code source.  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 Projet correspondant à ce répertoire est vide.  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)