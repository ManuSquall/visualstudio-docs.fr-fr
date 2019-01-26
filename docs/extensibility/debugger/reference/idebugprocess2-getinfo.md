---
title: IDebugProcess2::GetInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::GetInfo
helpviewer_keywords:
- IDebugProcess2::GetInfo
ms.assetid: 46021dce-bb97-46c3-b0cc-e5b3b68acc35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40c2630039fc5312e76b5bb4657673f2d3a3e9c2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54985131"
---
# <a name="idebugprocess2getinfo"></a>IDebugProcess2::GetInfo
Obtient une description du processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetInfo(  
   PROCESS_INFO_FIELDS  Fields,  
   PROCESS_INFO*        pProcessInfo  
);  
```  
  
```csharp  
int GetInfo(  
   enum_PROCESS_INFO_FIELDS  Fields,  
   PROCESS_INFO[]            pProcessInfo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `Fields`  
 [in] Une combinaison de valeurs à partir de la [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) énumération qui spécifie les champs de la `pProcessInfo` paramètre doivent être renseignés.  
  
 `pProcessInfo`  
 [out] Un [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) structure est remplie avec une description du processus.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)