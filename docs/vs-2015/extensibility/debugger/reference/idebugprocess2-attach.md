---
title: IDebugProcess2::Attach | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4dee9894985720e93367cae9c619dd77b24ba89b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833458"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Attache le Gestionnaire de session de débogage (SDM) au processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
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
 [in] Tableau de GUID des moteurs de débogage à utiliser pour déboguer des programmes en cours d’exécution dans le processus. Ce paramètre peut être une valeur null. Pour plus d’informations, consultez la section Notes.  
  
 `celtSpecificEngines`  
 [in] Le nombre de débogage moteurs dans le `rgguidSpecificEngines` tableau et la taille de la `rghrEngineAttach` tableau.  
  
 `rghrEngineAttach`  
 [in, out] Un tableau des codes HRESULT retourné par les moteurs de débogage. La taille de ce tableau est spécifiée dans le `celtSpecificEngines` paramètre. Chaque code est généralement `S_OK` ou `S_ATTACH_DEFERRED`. Ce dernier indique que l’Allemagne est actuellement attaché à aucun programme.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur. Le tableau suivant présente les autres valeurs possibles.  
  
|Value|Description|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Le processus spécifié est déjà attaché au débogueur.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Une violation de sécurité s’est produite lors de la procédure d’attachement.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Un processus de bureau ne peut pas être attaché au débogueur.|  
  
## <a name="remarks"></a>Notes  
 Attachement à un processus attache le SDM sur tous les programmes en cours d’exécution dans ce processus qui peuvent être débogué par les moteurs de débogage (dé) spécifiés dans le `rgguidSpecificEngines` tableau. Définir le `rgguidSpecificEngines` une valeur null au paramètre de valeur ou inclure `GUID_NULL` dans le tableau à attacher à tous les programmes dans le processus.  
  
 Tous les événements de débogage qui se produisent dans le processus sont envoyés à la donnée [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objet. Cela `IDebugEventCallback2` objet est fourni lorsque le SDM appelle cette méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

