---
title: ToggleHUD | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 87c2571926b92e59ae03e5e988bbf535474dc6d0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948907"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Active ou désactive les diagnostics graphiques *HUD* (Head-Up Display) de superposition ou désactiver.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Notes  
 Graphics diagnostics HUD s’affiche dans le coin supérieur gauche de l’application qui s’exécute dans graphics diagnostics. Il affiche des informations d’exécution sur l’application et capture des informations graphiques, ainsi que les messages qui sont ajoutés en appelant le [AddMessage](../debugger/addmessage.md) fonction membre.  
  
 Pour activer/désactiver le HUD, vous n’êtes pas obligé d’être activement capture d’informations graphiques, autrement dit, il peut être activé ou désactivé via une instance de la `VsgDbg` (classe), mais la [Init](../debugger/init.md) fonction membre n’a d’abord être appelées.
