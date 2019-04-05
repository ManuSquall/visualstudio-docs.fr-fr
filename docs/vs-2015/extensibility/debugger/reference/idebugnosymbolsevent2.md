---
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5d36b1091f34318ccba1ce0a997ad23043cbdeb2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950576"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Signale la [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] l’interface utilisateur pour l’avertir que les symboles ne peut pas être localisés pour l’exécutable de lancement du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Implémenté par les moteurs de débogage et consommé par le [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] l’interface utilisateur du débogueur.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
