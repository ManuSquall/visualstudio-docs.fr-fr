---
title: IDebugPortSupplierEx2::SetServer | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugPortSupplierEx2::SetServer
ms.assetid: 0e8ef194-3a4f-4abf-8382-4607ab3005d1
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1750d6891cf6bec2c78212ad5c7f9137247f9147
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugportsupplierex2setserver"></a>IDebugPortSupplierEx2::SetServer
Définit le serveur de base pour le fournisseur de port.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetServer(  
   IDebugCoreServer2* pServer  
);  
```  
  
```csharp  
int SetServer(  
   IDebugCoreServer2 pServer  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pServer`  
 Installation minimale à définir pour le fournisseur de port.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPortSupplierEx2](../../../extensibility/debugger/reference/idebugportsupplierex2.md)