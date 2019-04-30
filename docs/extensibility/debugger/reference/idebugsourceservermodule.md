---
title: IDebugSourceServerModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c40a2da886b4e999649349d4af306295c87863ff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916075"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Représente les informations du serveur source qui sont contenues dans un fichier PDB.

## <a name="syntax"></a>Syntaxe

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Cette interface est implémentée par les moteurs de débogage et utilisée par l’interface utilisateur du débogueur.

## <a name="methods"></a>Méthodes
 Le tableau suivant présente les méthodes de `IDebugSourceServerModule`.

|Méthode|Description|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Récupère un tableau d’informations du serveur source.|

## <a name="requirements"></a>Configuration requise
 En-tête : Msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll