---
title: IDebugSymbolProviderDirect | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcbee53b2f3d0a5a4fc45ab7e55bbb2a0cbe106a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931126"
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Représente un fournisseur de symbole qui a un accès direct aux interfaces de symbole de métadonnées et core.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugSymbolProviderDirect: IUnknown  
```  
  
## <a name="methods"></a>Méthodes  
 Cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Récupère l’identificateur de domaine d’application étant donné l’adresse de débogage.|  
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Récupère des informations sur les modules dans le groupe de symboles.|  
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Récupère des informations sur le groupe de symboles dont le fournisseur de symboles est un membre.|  
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Récupère les informations d’importation de métadonnées.|  
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Récupère des informations sur la méthode à l’adresse de débogage spécifié.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Récupère un lecteur de symboles du code non managé.|  
  
## <a name="remarks"></a>Notes  
 Cette interface peut être utilisée au lieu de la plupart des autres interfaces de fournisseur de symboles. Il offre un accès direct aux métadonnées et `CorSym` interfaces.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : SH.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll