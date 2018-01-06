---
title: IDebugAlias2::GetAppDomainId | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a8ddebc0f540be650650595e5b808c9c4b19f706
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
Récupère l’identificateur pour le domaine d’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAppDomainId (  
   ULONG32* pappDomainId  
);  
```  
  
```csharp  
int GetAppDomainId (  
   out uint pappDomainId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pappDomainId`  
 [out] Retourne l’identificateur du domaine d’application.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Les modifications d’identificateur de domaine application chaque fois que l’application est redémarrée et un domaine d’application est créé.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)