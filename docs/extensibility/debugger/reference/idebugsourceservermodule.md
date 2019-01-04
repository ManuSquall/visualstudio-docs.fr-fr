---
title: IDebugSourceServerModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fcdeac3d68b2b26f0613dc92b473a17ce2ffd122
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945793"
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
  
## <a name="requirements"></a>Spécifications  
 En-tête : Msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll