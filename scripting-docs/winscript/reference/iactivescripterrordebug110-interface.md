---
title: Interface IActiveScriptErrorDebug110 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 1bac0c15f31f12ae48f6669bf9a0853550f8c191
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150645"
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