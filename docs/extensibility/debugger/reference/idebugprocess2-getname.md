---
title: IDebugProcess2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::GetName
helpviewer_keywords:
- IDebugProcess2::GetName
ms.assetid: a2f66ab5-53e5-4cdc-a1b5-3b8afa8ee646
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8ae9fc5608a6dbb6aeb493ee5937b15aa346b636
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53960522"
---
# <a name="idebugprocess2getname"></a>IDebugProcess2::GetName
Obtient le titre, le nom convivial ou le nom de fichier du processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName(   
   GETNAME_TYPE  gnType,  
   BSTR*         pbstrName  
);  
```  
  
```csharp  
int GetName(   
   enum_GETNAME_TYPE  gnType,  
   out string         pbstrName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `gnType`  
 [in] Une valeur comprise entre le [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) énumération qui spécifie le type de nom à retourner.  
  
 `pbstrName`  
 [out] Retourne le nom du processus.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)