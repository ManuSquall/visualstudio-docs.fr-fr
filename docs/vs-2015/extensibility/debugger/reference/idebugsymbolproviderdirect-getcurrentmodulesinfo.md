---
title: IDebugSymbolProviderDirect::GetCurrentModulesInfo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetCurrentModulesInfo
- GetCurrentModulesInfo
ms.assetid: b3b45ed2-ea4e-4389-b78a-11fc9796a6c1
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4ce4473fca76424f3b737d530997f766da7b219d
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "62421913"
---
# <a name="idebugsymbolproviderdirectgetcurrentmodulesinfo"></a>IDebugSymbolProviderDirect::GetCurrentModulesInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Récupère des informations sur les modules dans le groupe de symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [in] Identificateurs pour les domaines d’application.  
  
 `pCurrentState`  
 [in] État actuel du groupe de symboles.  
  
 `ppCDModItfs`  
 [out] Retourne un objet qui contient les modules dans le groupe de symboles.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
