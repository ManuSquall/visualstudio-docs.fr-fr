---
title: IDebugCoreServer3::EnableAutoAttach | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d0b7fbfc1d7c3d9d4ab5214e8c0c5518c6dad5cb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Permet l’attachement automatique pour les moteurs de débogage spécifiés.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `rgguidSpecificEngines`  
 [in] Tableau de GUID pour chaque moteur de débogage à marquer comme l’attachement automatique.  
  
 `celtSpecificEngines`  
 [in] Le nombre de moteurs spécifié dans `rgguidSpecificEngines`.  
  
 `pszStartPageUrl`  
 [in] URL de démarrage à utiliser lors de l’attachement d’automatique.  
  
 `pbstrSessionID`  
 [out] ID de la session qui a été attaché automatiquement.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne le code d’erreur. Un code d’erreur est `E_AUTO_ATTACH_NOT_REGISTERED`, ce qui signifie que la fabrique de classe auto-attach n’a pas été inscrit.  
  
## <a name="remarks"></a>Notes  
 Lorsqu’un programme associé à l’URL spécifiée est démarré, les moteurs de débogage spécifiés sont automatiquement démarrés et attachés.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)