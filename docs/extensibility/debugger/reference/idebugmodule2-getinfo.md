---
title: IDebugModule2::GetInfo | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugModule2::GetInfo method
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 859a85b51e83d438ea4051e2506c2dc0696768b8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820679"
---
# <a name="idebugmodule2getinfo"></a>IDebugModule2::GetInfo
Obtient des informations sur ce module.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwFields`  
 [in] Une combinaison d’indicateurs de la [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) énumération qui spécifient les champs de `pInfo` doivent être remplis.  
  
 `pInfo`  
 [in, out] Un [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) structure est remplie avec une description du module.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Le [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) structure contient le nom du module qui s’affiche dans le **Modules** fenêtre.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE_INFO_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)