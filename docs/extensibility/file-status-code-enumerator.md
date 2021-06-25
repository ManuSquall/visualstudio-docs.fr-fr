---
title: Énumérateur de code d’état de fichier | Microsoft Docs
description: L’énumérateur SccStatus contient des valeurs constantes qui spécifient l’état d’un fichier dans le système de contrôle de code source et qui est utilisé par SccQueryInfo et POPLISTFUNC.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 95de8a29efcd56880cdaf452c9f21b90bba1c5c9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900965"
---
# <a name="file-status-code-enumerator"></a>Énumérateur de code d’état de fichier
L' `SccStatus` énumérateur contient des valeurs constantes nommées qui spécifient l’état d’un fichier dans le système de contrôle de code source. Cette énumération est utilisée par [SccQueryInfo](../extensibility/sccqueryinfo-function.md) et la `POPLISTFUNC` fonction de rappel (pour plus d’informations, consultez [POPLISTFUNC](../extensibility/poplistfunc.md) ).

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
 Impossible d’obtenir l’état de l’SCC_STATUS_INVALID ; ne vous fiez pas à cette fonction.

 SCC_STATUS_NOTCONTROLLED fichier n’est pas sous contrôle de code source.

 SCC_STATUS_CONTROLLED fichier est sous contrôle de code source.

 SCC_STATUS_CHECKEDOUT extrait par l’utilisateur actuel sur le disque local.

 SCC_STATUS_OUTOTHER fichier est extrait par un autre utilisateur.

 SCC_STATUS_OUTEXCLUSIVE fichier est extrait en mode exclusif.

 SCC_STATUS_OUTMULTIPLE fichier est extrait par plusieurs utilisateurs.

 SCC_STATUS_OUTOFDATE le fichier n’est pas le plus récent.

 SCC_STATUS_DELETED fichier a été supprimé du projet.

 Le fichier SCC_STATUS_LOCKED est verrouillé ; aucune autre version n’est autorisée.

 SCC_STATUS_MERGED fichier a été fusionné mais pas encore résolu/vérifié.

 SCC_STATUS_SHARED fichier est partagé entre les projets.

 SCC_STATUS_PINNED fichier est partagé dans une version explicite.

 SCC_STATUS_MODIFIED fichier a été modifié/cassé/violé.

 SCC_STATUS_OUTBYUSER fichier est extrait par l’utilisateur actuel.

 SCC_STATUS_NOMERGE fichier ne peut jamais être fusionné avec et ne doit pas être enregistré avant une opération d’extraction.

 SCC_STATUS_RESERVED_1 réservé à un usage interne.

 SCC_STATUS_RESERVED_2 réservé à un usage interne.

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
