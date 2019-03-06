---
title: Interface IActiveScriptErrorDebug110 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug110 Interface
ms.assetid: 5c1a4993-4cad-4ccf-89c2-53abfddfe1f2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 067a62ec8b87c448577cfd6e5789ae5e073b5fb8
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345901"
---
# <a name="iactivescripterrordebug110-interface"></a>IActiveScriptErrorDebug110 (interface)
Ajoute des fonctionnalités à la [IActiveScriptDebug (Interface)](../../winscript/reference/iactivescriptdebug-interface.md). Cette interface est implémentée par le moteur JavaScript pour déterminer pourquoi un événement BREAKREASON_ERROR s'est produit.  
  
> [!IMPORTANT]
>  Elle est implémentée par PDM version v11.0 et supérieures. Trouvée dans activdbg100.h.  
  
## <a name="methods"></a>Méthodes  
 L'interface `IActiveScriptErrorDebug110` expose les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)|Retourne le type d'exception d'une exception levée.|