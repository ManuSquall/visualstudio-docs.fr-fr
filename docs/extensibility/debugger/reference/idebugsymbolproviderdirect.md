---
title: IDebugSymbolProviderDirect - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd1201007b27d3c7c51b5b0d862b36ba0549429b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718902"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Représente un fournisseur de symboles qui a un accès direct aux métadonnées et aux interfaces de symbole de base.

## <a name="syntax"></a>Syntaxe

```
IDebugSymbolProviderDirect: IUnknown
```

## <a name="methods"></a>Méthodes
 Cette interface met en œuvre les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Récupère l’identifiant de domaine d’application compte tenu de l’adresse de débogé.|
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Récupère des informations sur les modules dans le groupe de symboles.|
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Récupère des informations sur le groupe de symboles dont le fournisseur de symboles est membre.|
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Récupère les informations d’importation de métadonnées.|
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Récupère des informations sur la méthode à l’adresse de débogé spécifiée.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Récupère un lecteur de symbole pour le code non menté.|

## <a name="remarks"></a>Notes
 Cette interface peut être utilisée au lieu de la plupart des autres interfaces de fournisseur de symboles. Il offre un accès direct `CorSym` aux métadonnées et aux interfaces.

## <a name="requirements"></a>Spécifications
 En-tête: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
