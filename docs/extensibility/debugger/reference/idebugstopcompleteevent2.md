---
title: IDebugStopCompleteEvent2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 55061440f4690c9b9f9b7a90dc5474391f908046
ms.lasthandoff: 02/22/2017

---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
Le moteur de débogage (DE) peut envoyer cet événement facultatif pour le Gestionnaire de session de débogage (SDM) lorsqu’un programme s’est arrêté.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes relatives à l’attention des implémenteurs  
 Il s’agit d’une nouvelle interface pour [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]. Les versions antérieures ne prenaient pas en charge l’arrêt asynchrone.  
  
 [Arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) est appelée par le SDM dans des scénarios à plusieurs processus ou programme multiples. Lorsqu’un programme envoie un événement d’arrêt pour le SDM, le SDM demande arrêter trop d’autres programmes.  
  
 Il est utilisé pour informer de façon asynchrone le SDM un programme s’est arrêté. Cela est utile pour un moteur de débogage interpréteur, où parfois aucun code n’est en cours d’exécution du programme débogué, donc [arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) ne peut pas être effectuée de façon synchrone. Si un moteur de débogage souhaite employer cette notification asynchrone, elle doit retourner `S_ASYNC_STOP` de [arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
