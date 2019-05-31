---
title: Énumérateur de Code de statut de répertoire | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b6e113949c9e87605895bbb43aa1ae4b4df0496
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66348035"
---
# <a name="directory-status-code-enumerator"></a>Énumérateur de code de statut de répertoire
Le `SccDirStatus` énumérateur contient des valeurs de constantes nommées qui spécifient l’état d’un répertoire dans le système de contrôle source. Cette énumération est utilisée par le [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Cela a été introduite dans la version 1.2 de l’API de plug-in de contrôle de Source.

## <a name="syntax"></a>Syntaxe

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>Membres
 État de SCC_DIRSTATUS_INVALID n’a pas pu être obtenu ; ne comptez pas sur celle-ci.

 Répertoire de SCC_DIRSTATUS_NOTCONTROLLED n’est pas sous contrôle de code source.

 Répertoire de SCC_DIRSTATUS_CONTROLLED est sous contrôle de code source.

 Projet SCC_DIRSTATUS_EMPTYPROJ correspondant à ce répertoire est vide.

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)