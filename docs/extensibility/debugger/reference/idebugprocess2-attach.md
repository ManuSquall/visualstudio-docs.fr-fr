---
title: IDebugProcess2::Attach | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::Attach
helpviewer_keywords: IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 47b14c3de6b5b9980e2ad420596a1243e84c8882
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Attache le Gestionnaire de session de débogage (SDM) au processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pCallback`  
 [in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objet qui est utilisé pour la notification d’événement de débogage.  
  
 `rgguidSpecificEngines`  
 [in] Un tableau des GUID des moteurs de débogage à utiliser pour déboguer des programmes en cours d’exécution dans le processus. Ce paramètre peut être une valeur null. Pour plus d’informations, consultez la section Notes.  
  
 `celtSpecificEngines`  
 [in] Le nombre de débogage moteurs dans le `rgguidSpecificEngines` tableau et la taille de la `rghrEngineAttach` tableau.  
  
 `rghrEngineAttach`  
 [dans, out] Tableau des codes HRESULT retourné par les moteurs de débogage. La taille de ce tableau est spécifiée dans le `celtSpecificEngines` paramètre. Chaque code est généralement `S_OK` ou `S_ATTACH_DEFERRED`. Ce dernier indique que la D’est actuellement attachée à aucun programme.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le tableau suivant répertorie les autres valeurs possibles.  
  
|Value|Description|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Le processus spécifié est déjà attaché au débogueur.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Une violation de sécurité s’est produite lors de la procédure d’attachement.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Un processus ne peut pas être attaché au débogueur.|  
  
## <a name="remarks"></a>Notes  
 Attachement à un processus attache le SDM sur tous les programmes en cours d’exécution dans ce processus peut être débogué par les moteurs de débogage (DE) spécifiés dans le `rgguidSpecificEngines` tableau. Définir le `rgguidSpecificEngines` une valeur null au paramètre de valeur ou inclure `GUID_NULL` dans le tableau à attacher à tous les programmes dans le processus.  
  
 Tous les événements de débogage qui se produisent dans le processus sont envoyées à la donnée [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objet. Cela `IDebugEventCallback2` objet est fourni lorsque le SDM appelle cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)