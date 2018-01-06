---
title: IDebugSymbolProviderDirect | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugSymbolProviderDirect interface
ms.assetid: 872b04a8-70de-4ab5-aceb-684c81828545
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a5b2e91a43be7ed1a605e4f54211b2acc5e2df8d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsymbolproviderdirect"></a>IDebugSymbolProviderDirect
Représente un fournisseur de symbole qui a un accès direct aux interfaces de symbole de métadonnées et de noyau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugSymbolProviderDirect: IUnknown  
```  
  
## <a name="methods"></a>Méthodes  
 Cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetAppIDFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getappidfromaddress.md)|Récupère l’identificateur de domaine d’application étant donné l’adresse de débogage.|  
|[GetCurrentModulesInfo](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesinfo.md)|Récupère les informations sur les modules dans le groupe de symboles.|  
|[GetCurrentModulesState](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getcurrentmodulesstate.md)|Récupère les informations sur le groupe de symbole dont le fournisseur de symbole est un membre.|  
|[GetMetaDataImport](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmetadataimport.md)|Récupère les informations d’importation de métadonnées.|  
|[GetMethodFromAddress](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getmethodfromaddress.md)|Récupère les informations sur la méthode à l’adresse de débogage spécifiés.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugsymbolproviderdirect-getsymunmanagedreader.md)|Récupère un lecteur de symboles pour le code non managé.|  
  
## <a name="remarks"></a>Notes  
 Cette interface peut être utilisée au lieu de la plupart des autres interfaces de fournisseur de symboles. Il fournit un accès direct aux métadonnées et `CorSym` interfaces.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll