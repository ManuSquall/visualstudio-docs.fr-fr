---
title: IDebugCoreServer3::EnableAutoAttach | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bf32eb5d8771f95ec155a93d1fe1e770e0cc2d52
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108493"
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