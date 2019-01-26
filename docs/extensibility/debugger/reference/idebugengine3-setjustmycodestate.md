---
title: IDebugEngine3::SetJustMyCodeState | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 180ef79d488585aa50eb19da6924c642340d0aa7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925992"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
Cette méthode indique au moteur de débogage sur les informations d’état JustMyCode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
);  
```  
  
```csharp  
int SetJustMyCodeState(  
   int             fUpdate,   
   uint            dwModules,   
   JMC_CODE_SPEC[] rgJMCSpec  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fUpdate`  
 [in] Différent de zéro (`TRUE`) pour mettre à jour les informations actuelles, zéro (`FALSE`) pour réinitialiser toutes les informations (en ignorant quoi que ce soit défini précédemment).  
  
 `dwModules`  
 [in] Nombre de structures d’informations dans `rgJMCSpec.`  
  
 `rgJMCSpec`  
 [in] Tableau de [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) structures à utiliser.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne le code d’erreur.  
  
## <a name="remarks"></a>Notes  
 JustMyCode est le concept de débogage uniquement du code qui appartient à un utilisateur et en ignorant tout le code intermédiaire tel que le code du système, même si le code source est disponible pour le code de ce système.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)