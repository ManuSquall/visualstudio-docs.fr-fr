---
title: 'IDebugEngine3 :: SetJustMyCodeState | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetJustMyCodeState
helpviewer_keywords:
- IDebugEngine3::SetJustMyCodeState
ms.assetid: 8ec17fbf-df93-424a-b2ed-fd1e5ee51256
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebaf697bfdfff435c12eee1002ff93f4eba7ed65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195861"
---
# <a name="idebugengine3setjustmycodestate"></a>IDebugEngine3::SetJustMyCodeState
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette méthode indique au moteur de débogage à propos des informations d’état JustMyCode.  
  
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
 dans Différent de zéro ( `TRUE` ) pour mettre à jour les informations actuelles, zéro ( `FALSE` ) pour réinitialiser toutes les informations (sans tenir compte des éléments précédemment définis).  
  
 `dwModules`  
 dans Nombre de structures d’informations dans `rgJMCSpec.`  
  
 `rgJMCSpec`  
 dans Tableau de structures de [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) à utiliser.  
  
## <a name="return-value"></a>Valeur renvoyée  
 En cas de réussite, retourne `S_OK` ; sinon, retourne le code d’erreur.  
  
## <a name="remarks"></a>Notes  
 JustMyCode est le concept qui consiste à déboguer uniquement le code qui appartient à un utilisateur et à ignorer tout le code intermédiaire tel que le code système, même si le code source est disponible pour ce code système.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)   
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)
