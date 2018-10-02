---
title: IDebugEngine3::SetJustMyCodeState | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e612b39bb71465aff50095dfeecf01cd025c4f2d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501437"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugEngine3::SetJustMyCodeState](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugengine3-setjustmycodestate).  
  
Cette méthode indique au moteur de débogage sur les informations d’état JustMyCode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetJustMyCodeState(  
   BOOL           fUpdate,  
   DWORD          dwModules,  
   JMC_CODE_SPEC* rgJMCSpec  
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

