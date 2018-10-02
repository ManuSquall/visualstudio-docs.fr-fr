---
title: Énumérateur de Code de statut de répertoire | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 24f6dde65def4569eb8163d281f872011be0275c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507328"
---
# <a name="directory-status-code-enumerator"></a>Énumérateur de code d’état de répertoire
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [énumérateur de Code d’état Directory](https://docs.microsoft.com/visualstudio/extensibility/directory-status-code-enumerator).  
  
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

