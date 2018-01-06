---
title: IDebugStopCompleteEvent2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5d59de29078db46f716fe9d01a3f3fa076139ddf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
Le moteur de débogage (DE) peut envoyer cet événement facultatif pour le Gestionnaire de session de débogage (SDM) lorsqu’un programme s’est arrêté.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Il s’agit d’une nouvelle interface pour [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]. Les versions antérieures ne prenaient pas en charge l’arrêt asynchrone.  
  
 [Arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) est appelée par le SDM dans plusieurs processus ou programme plusieurs scénarios. Lorsqu’un programme envoie un événement d’arrêt pour le SDM, le SDM demande arrêter trop des autres programmes.  
  
 Il permet d’indiquer de façon asynchrone le SDM un programme s’est arrêté. Cela est utile pour un moteur de débogage interpréteur, où parfois aucun code n’est en cours d’exécution du programme débogué, donc [arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) ne peut pas être effectuée de façon synchrone. Si un moteur de débogage veut employer cette notification asynchrone, elle doit retourner `S_ASYNC_STOP` de [arrêter](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll