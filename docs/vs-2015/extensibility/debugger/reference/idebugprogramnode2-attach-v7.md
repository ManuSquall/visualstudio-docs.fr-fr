---
title: IDebugProgramNode2::Attach_V7 | Microsoft Docs
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
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
ms.assetid: b5ffc736-efc7-4ca8-964d-5536ff891b0e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55a13bbfa3b2addbeb05b343dae5f598ddaac687
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260739"
---
# <a name="idebugprogramnode2attachv7"></a>IDebugProgramNode2::Attach_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

DÉCONSEILLÉ. N’UTILISEZ PAS.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT Attach_V7 (   
   IDebugProgram2*       pMDMProgram,  
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason  
);  
```  
  
```csharp  
int Attach_V7 (   
   IDebugProgram2       pMDMProgram,  
   IDebugEventCallback2 pCallback,  
   uint                 dwReason  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pMDMProgram`  
 [in] Le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface qui représente le programme à attacher.  
  
 `pCallback`  
 [in] Le [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) interface à utiliser pour envoyer des événements de débogage vers le SDM.  
  
 `dwReason`  
 [in] Une valeur comprise entre le [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) énumération qui spécifie la raison de l’attachement.  
  
## <a name="return-value"></a>Valeur de retour  
 Une implémentation doit toujours retourner `E_NOTIMPL`.  
  
## <a name="remarks"></a>Notes  
  
> [!WARNING]
>  En tant que de [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], cette méthode n’est plus utilisée et doit toujours retourner `E_NOTIMPL`. Consultez le [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) interface pour une autre approche, si le nœud de programme a besoin indiquer qu’il ne peut pas être attachée à ou si le nœud de programme consiste simplement à définir le programme `GUID`. Sinon, implémenter la [attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md) (méthode).  
  
## <a name="prior-to-visual-studio-2005"></a>Avant Visual Studio 2005  
 Cette méthode doit être implémentée uniquement si le DE s’exécute dans l’espace d’adressage du programme en cours de débogage. Sinon, cette méthode doit retourner `S_FALSE`.  
  
 Lorsque cette méthode est appelée, l’Allemagne doit envoyer le [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) objet d’événement, si elle n’a pas déjà été envoyé pour cette instance de la [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interface, mais aussi le [ IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) et [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) objets événement. Le [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) objet d’événement est ensuite envoyé si le `dwReason` paramètre est `ATTACH_REASON_LAUNCH`.  
  
 Le DE doit appeler le [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) méthode sur le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objet fourni par le [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) événements de l’objet et devez stocker les GUID de ce programme dans les données d’instance pour le `IDebugProgram2` objet implémenté par l’Allemagne.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)

