---
title: IDebugSymbolProviderDirect::GetCurrentModulesInfo | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetCurrentModulesInfo
- GetCurrentModulesInfo
ms.assetid: b3b45ed2-ea4e-4389-b78a-11fc9796a6c1
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 86bdbf5d998f40bcd844939e07c898ae41bfd1a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesinfo"></a>IDebugSymbolProviderDirect::GetCurrentModulesInfo
Récupère les informations sur les modules dans le groupe de symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCurrentModulesInfo(  
   unsigned long * pCount,  
   GUID *          ppGuids,  
   DWORD *         pADIds,  
   DWORD *         pCurrentState,  
   IUnknown **     ppCDModItfs  
);  
```  
  
```csharp  
int GetCurrentModulesInfo(  
   uint       pCount,  
   Guid       ppGuids,  
   uint       pADIds,  
   uint       pCurrentState,  
   out object ppCDModItfs  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pCount`  
 [in] Nombre de modules dans le `ppGuids` tableau.  
  
 `ppGuids`  
 [in] Tableau qui contient les identificateurs uniques pour les modules.  
  
 `pADIds`  
 [in] Identificateurs des domaines d’application.  
  
 `pCurrentState`  
 [in] État actuel du groupe de symboles.  
  
 `ppCDModItfs`  
 [out] Retourne un objet qui contient les modules dans le groupe de symboles.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)