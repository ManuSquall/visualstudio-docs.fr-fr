---
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 179d8a95bc54db90a98311626b34c3e17b68f7f0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53873117"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Signale la [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur pour l’avertir que les symboles ne peut pas être localisés pour l’exécutable de lancement du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Implémenté par les moteurs de débogage et consommé par le [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur du débogueur.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll