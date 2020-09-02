---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2a6a6e69bf47751706710801dd78c832ccd2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546917"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Le moteur DE débogage (DE) peut envoyer cet événement facultatif au gestionnaire de débogage de session (SDM) lorsqu’un programme s’est arrêté.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Il s’agit d’une nouvelle interface pour [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] . Les versions antérieures ne prenaient pas en charge l’arrêt asynchrone.  
  
 L' [arrêt](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) est appelé par le SDM dans des scénarios à plusieurs processus ou à plusieurs programmes. Lorsqu’un programme envoie un événement d’arrêt au SDM, le SDM demande également l’arrêt d’autres programmes.  
  
 Il est utilisé pour informer de manière asynchrone le SDM qu’un programme s’est arrêté. Cela est utile pour un moteur de débogage de l’interpréteur, où aucun code n’est parfois exécuté à l’intérieur du programme débogué. l' [arrêt](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) ne peut donc pas être effectué de façon synchrone. Si un moteur de débogage souhaite utiliser cette notification asynchrone, il doit retourner `S_ASYNC_STOP` à partir de [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
