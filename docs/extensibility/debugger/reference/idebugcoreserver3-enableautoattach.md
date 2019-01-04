---
title: IDebugCoreServer3::EnableAutoAttach | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 2477ac13218342511ac7b47bec6cf847651cfb22
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913068"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
Permet l’attachement automatique pour les moteurs de débogage spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `rgguidSpecificEngines`  
 [in] Tableau de GUID pour chaque moteur de débogage pour marquer comme l’attachement automatique.  
  
 `celtSpecificEngines`  
 [in] Le nombre de moteurs spécifié dans `rgguidSpecificEngines`.  
  
 `pszStartPageUrl`  
 [in] URL de démarrage à utiliser lors de l’attachement d’automatique.  
  
 `pbstrSessionID`  
 [out] ID de la session qui a été attaché à automatique.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne le code d’erreur. Un code d’erreur est `E_AUTO_ATTACH_NOT_REGISTERED`, ce qui indique que la fabrique de classe auto-attach n’a pas été inscrit.  
  
## <a name="remarks"></a>Notes  
 Lorsqu’un programme associé à l’URL spécifiée est démarré, les moteurs de débogage spécifié sont automatiquement démarrés et attachés.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)