---
title: Enumérateur de code d’état de fichier ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 184c8686ea184aea2cbd0a64873718cbe72f7615
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711455"
---
# <a name="file-status-code-enumerator"></a>Enumérateur de code de statut de fichier
L’enumérateur `SccStatus` contient des valeurs constantes nommées qui spécifient l’état d’un fichier dans le système de contrôle source. Cette énumération est utilisée par le [SccQueryInfo](../extensibility/sccqueryinfo-function.md) et la `POPLISTFUNC` fonction de rappel (voir [POPLISTFUNC](../extensibility/poplistfunc.md) pour plus de détails).

## <a name="syntax"></a>Syntaxe

```
enum SccStatus {
   SCC_STATUS_INVALID          = -1L,
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,
   SCC_STATUS_CONTROLLED       = 0x0001L,
   SCC_STATUS_CHECKEDOUT       = 0x0002L,
   SCC_STATUS_OUTOTHER         = 0x0004L,
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,
   SCC_STATUS_OUTOFDATE        = 0x0020L,
   SCC_STATUS_DELETED          = 0x0040L,
   SCC_STATUS_LOCKED           = 0x0080L,
   SCC_STATUS_MERGED           = 0x0100L,
   SCC_STATUS_SHARED           = 0x0200L,
   SCC_STATUS_PINNED           = 0x0400L,
   SCC_STATUS_MODIFIED         = 0x0800L,
   SCC_STATUS_OUTBYUSER        = 0x1000L
   SCC_STATUS_NOMERGE          = 0x2000L
   SCC_STATUS_RESERVED_1       = 0x4000L
   SCC_STATUS_RESERVED_2       = 0x8000L
};
```

## <a name="members"></a>Membres
 SCC_STATUS_INVALID Statut n’a pu être obtenu; ne s’y fient pas.

 SCC_STATUS_NOTCONTROLLED Fichier n’est pas sous contrôle source.

 SCC_STATUS_CONTROLLED Fichier est sous contrôle source.

 SCC_STATUS_CHECKEDOUT Vérifié par l’utilisateur actuel sur le disque local.

 SCC_STATUS_OUTOTHER Fichier est vérifié par un autre utilisateur.

 SCC_STATUS_OUTEXCLUSIVE Fichier est exclusivement vérifié.

 SCC_STATUS_OUTMULTIPLE Fichier est vérifié par plus d’un utilisateur.

 SCC_STATUS_OUTOFDATE Le fichier n’est pas le plus récent.

 SCC_STATUS_DELETED File a été supprimé du projet.

 SCC_STATUS_LOCKED Fichier est verrouillé; plus de versions autorisées.

 SCC_STATUS_MERGED File a été fusionné mais n’a pas encore été corrigé/vérifié.

 SCC_STATUS_SHARED Fichier est partagé entre les projets.

 SCC_STATUS_PINNED Fichier est partagé sur une version explicite.

 SCC_STATUS_MODIFIED Fichier a été modifié/brisé/violé.

 SCC_STATUS_OUTBYUSER Fichier est vérifié par l’utilisateur actuel.

 SCC_STATUS_NOMERGE Fichier ne peut jamais être fusionné avec et n’a pas besoin d’être enregistré avant un GET.

 SCC_STATUS_RESERVED_1 Réservé à un usage interne.

 SCC_STATUS_RESERVED_2 Réservé à un usage interne.

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle des sources](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)
