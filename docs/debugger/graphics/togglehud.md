---
title: ToggleHUD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e49066d4625990119159ea72f59a3a3fe59d581c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953300"
---
# <a name="togglehud"></a>ToggleHUD
Active ou désactive les diagnostics graphiques *HUD* (Head-Up Display) de superposition ou désactiver.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Remarques  
 Graphics diagnostics HUD s’affiche dans le coin supérieur gauche de l’application qui s’exécute dans graphics diagnostics. Il affiche des informations d’exécution sur l’application et capture des informations graphiques, ainsi que les messages qui sont ajoutés en appelant le [AddMessage](addmessage.md) fonction membre.  
  
 Pour activer/désactiver le HUD, vous n’êtes pas obligé d’être activement capture d’informations graphiques, autrement dit, il peut être activé ou désactivé via une instance de la `VsgDbg` (classe), mais la [Init](init.md) fonction membre n’a d’abord être appelées.