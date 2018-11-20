---
title: Arrêt et détachement | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b1641a9a44a3f37b07e8192169e7301153881484
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773871"
---
# <a name="termination-and-detaching"></a>Arrêt et détachement
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La section suivante décrit une fin normale.  
  
## <a name="discussion"></a>Discussion  
 Après le [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) interface se poursuit, si aucun des points d’arrêt, exceptions, erreurs d’exécution, ou les boucles infinies dans l’application à déboguer, le programme en cours de débogage s’exécute jusqu'à son achèvement. Il s’agit d’une fin normale.  
  
 Vous devez envoyer un [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) pour implémenter une fin normale. Cela requiert l’implémentation la [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)

