---
title: Énumérateur de code d’état de répertoire | Microsoft Docs
description: L’énumérateur SccDirStatus contient des valeurs constantes nommées qui spécifient l’état d’un répertoire dans le système de contrôle de code source et qui est utilisé par SccDirQueryInfo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3e995fb1dcb879645f59d6d8750852a790c99e90
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091251"
---
# <a name="directory-status-code-enumerator"></a>Énumérateur de code d’état de répertoire
L' `SccDirStatus` énumérateur contient des valeurs constantes nommées qui spécifient l’état d’un répertoire dans le système de contrôle de code source. Cette énumération est utilisée par [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Cela a été introduit dans la version 1,2 de l’API de plug-in de contrôle de code source.

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
 Impossible d’obtenir l’état de l’SCC_DIRSTATUS_INVALID ; ne vous fiez pas à cette fonction.

 SCC_DIRSTATUS_NOTCONTROLLED répertoire n’est pas sous contrôle de code source.

 SCC_DIRSTATUS_CONTROLLED répertoire est sous contrôle de code source.

 SCC_DIRSTATUS_EMPTYPROJ projet correspondant à ce répertoire est vide.

## <a name="see-also"></a>Voir aussi
- [Plug-ins de contrôle de code source](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
