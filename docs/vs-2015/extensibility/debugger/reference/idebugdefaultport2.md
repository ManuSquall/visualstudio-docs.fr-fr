---
title: IDebugDefaultPort2 | Microsoft Docs
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
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9367968f08116a21ea51fc1d0167fa57a5e3bd7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724492"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface fournit plusieurs méthodes pour accéder à serveur d’un port et les fonctionnalités de notification.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Visual Studio implémente cette interface pour représenter le port de débogage pour l’accès à des programmes. Un fournisseur de port personnalisé peut également implémenter cette interface si elle gère le débogage à distance.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Un argument à des méthodes sur le [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interface fournit cette interface. Appel [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) sur un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interface peut également obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
 Outre les méthodes définies dans [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Obtient l’interface de notification de port à partir de ce port.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Obtient l’interface pour le serveur qui héberge ce port.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Détermine si ce port est en cours d’exécution sur l’ordinateur local.|  
  
## <a name="remarks"></a>Notes  
 Le nom «`IDebugDefaultPort2`» est un peu trompeur, car il ne représente pas un port par défaut. Il peut être appelée « IDebugPort3 ».  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)

