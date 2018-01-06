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
ms.workload: vssdk
ms.openlocfilehash: 3cb8d93e39540a9f78da15902f821972914c0477
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
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