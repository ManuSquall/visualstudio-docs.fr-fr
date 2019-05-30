---
title: Énumérateur de Code d’état de fichier | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94bd9ff93872139fc056c4c8bb7a59191616919e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342687"
---
# <a name="file-status-code-enumerator"></a>Énumérateur de code de statut de fichier
Le `SccStatus` énumérateur contient des valeurs de constantes nommées qui spécifient l’état d’un fichier dans le système de contrôle source. Cette énumération est utilisée par le [SccQueryInfo](../extensibility/sccqueryinfo-function.md) et `POPLISTFUNC` fonction de rappel (voir [POPLISTFUNC](../extensibility/poplistfunc.md) pour plus d’informations).

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
 État de SCC_STATUS_INVALID n’a pas pu être obtenu ; ne comptez pas sur celle-ci.

 Fichier de SCC_STATUS_NOTCONTROLLED n’est pas sous contrôle de code source.

 SCC_STATUS_CONTROLLED fichier est sous contrôle de code source.

 SCC_STATUS_CHECKEDOUT vérifié au moyen de l’utilisateur actuel sur le disque local.

 SCC_STATUS_OUTOTHER fichier est extrait par un autre utilisateur.

 SCC_STATUS_OUTEXCLUSIVE fichier est extrait en mode exclusif.

 SCC_STATUS_OUTMULTIPLE fichier est extrait par plusieurs utilisateurs.

 SCC_STATUS_OUTOFDATE le fichier n’est pas la plus récente.

 Fichier de SCC_STATUS_DELETED a été supprimé du projet.

 SCC_STATUS_LOCKED fichier est verrouillé ; aucune version plus autorisée.

 SCC_STATUS_MERGED fichier a été fusionné mais pas encore résolu/vérifié.

 Fichier de SCC_STATUS_SHARED est partagé entre les projets.

 SCC_STATUS_PINNED fichier est partagé sur une version explicite.

 Fichier de SCC_STATUS_MODIFIED a été modifié, rompu/violée.

 SCC_STATUS_OUTBYUSER fichier est extrait par l’utilisateur actuel.

 Fichier de SCC_STATUS_NOMERGE ne peuvent jamais être fusionnée avec et ne doivent pas être enregistré avant une opération GET.

 SCC_STATUS_RESERVED_1 réservé à un usage interne.

 SCC_STATUS_RESERVED_2 réservé à un usage interne.

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)