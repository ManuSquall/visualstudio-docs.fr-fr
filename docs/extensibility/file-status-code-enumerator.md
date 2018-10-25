---
title: Énumérateur de Code d’état de fichier | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 884c7ab1b5d4fe1461fd1ae00fbc670f0bc7b6f2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921013"
---
# <a name="file-status-code-enumerator"></a>Énumérateur de code de statut de fichier
Le `SccStatus` énumérateur contient des valeurs de constantes nommées qui spécifient l’état d’un fichier dans le système de contrôle source. Cette énumération est utilisée par le [SccQueryInfo](../extensibility/sccqueryinfo-function.md) et `POPLISTFUNC` fonction de rappel (voir [POPLISTFUNC](../extensibility/poplistfunc.md) pour plus d’informations).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## <a name="members"></a>Membres  
 SCC_STATUS_INVALID  
 État n’a pas pu être obtenu ; ne comptez pas sur celle-ci.  
  
 SCC_STATUS_NOTCONTROLLED  
 Fichier n’est pas sous contrôle de code source.  
  
 SCC_STATUS_CONTROLLED  
 Fichier est sous contrôle de code source.  
  
 SCC_STATUS_CHECKEDOUT  
 Extrait par l’utilisateur actuel sur le disque local.  
  
 SCC_STATUS_OUTOTHER  
 Fichier est extrait par un autre utilisateur.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 Fichier est extrait en mode exclusif.  
  
 SCC_STATUS_OUTMULTIPLE  
 Fichier est extrait par plusieurs utilisateurs.  
  
 SCC_STATUS_OUTOFDATE  
 Le fichier n’est pas la plus récente.  
  
 SCC_STATUS_DELETED  
 Fichier a été supprimé du projet.  
  
 SCC_STATUS_LOCKED  
 Fichier est verrouillé ; aucune version plus autorisée.  
  
 SCC_STATUS_MERGED  
 Fichier a été fusionné mais pas encore résolu/vérifié.  
  
 SCC_STATUS_SHARED  
 Fichier est partagé entre les projets.  
  
 SCC_STATUS_PINNED  
 Fichier est partagé sur une version explicite.  
  
 SCC_STATUS_MODIFIED  
 Fichier a été modifié, rompu/violée.  
  
 SCC_STATUS_OUTBYUSER  
 Fichier est extrait par l’utilisateur actuel.  
  
 SCC_STATUS_NOMERGE  
 Fichier ne peut jamais être fusionnée avec et ne doive pas être enregistré avant une opération GET.  
  
 SCC_STATUS_RESERVED_1  
 Réservé à un usage interne.  
  
 SCC_STATUS_RESERVED_2  
 Réservé à un usage interne.  
  
## <a name="see-also"></a>Voir aussi  
 [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)