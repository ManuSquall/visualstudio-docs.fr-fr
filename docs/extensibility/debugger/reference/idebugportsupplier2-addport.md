---
title: IDebugPortSupplier2::AddPort | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier2::AddPort
helpviewer_keywords: IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6f77b0dd072c0e1acdbe642a0ded64a554f809f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
Ajoute un port.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT AddPort(   
   IDebugPortRequest2* pRequest,  
   IDebugPort2**       ppPort  
);  
```  
  
```csharp  
int AddPort(   
   IDebugPortRequest2 pRequest,  
   out IDebugPort2    ppPort  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pRequest`  
 [in] Un [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) objet qui décrit le port doit être ajouté.  
  
 `ppPort`  
 [out] Retourne un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) objet qui représente le port.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode crée le port demandé ainsi que l’ajouter à la liste d’interne du fournisseur de port de ports actifs. Le [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) méthode peut être appelée en premier pour éviter des retards de longue durées possible.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)