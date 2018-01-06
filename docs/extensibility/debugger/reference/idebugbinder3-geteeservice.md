---
title: IDebugBinder3::GetEEService | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder3::GetEEService
helpviewer_keywords: IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: fbebf4a70c8e22fda39e9b20e56ca6192f81a00e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Cette méthode retourne le service demandé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```csharp  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `vendor`  
 [in] `GUID` d’un fournisseur (une valeur null est acceptable).  
  
 `language`  
 [in] `GUID` d’une langue (une valeur null est acceptable).  
  
 `iid`  
 [in] `IID` du service à obtenir.  
  
 `ppService`  
 [out] Une interface pour le service demandé.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Passez le `IID` pour le [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) interface (`IID_IEEVisualizerServiceProvider`) pour voir si le service de visualiseur de Type est disponible. Si, par conséquent, l’évaluateur d’expression peut obtenir le [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) interface pour prendre en charge les visualiseurs de types. Consultez [Visualizing et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [Visualisation et affichage des données](../../../extensibility/debugger/visualizing-and-viewing-data.md)