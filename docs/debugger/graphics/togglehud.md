---
title: ToggleHUD | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86ce582ab49d4d079f01f7231f49aa761baa1069
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472511"
---
# <a name="togglehud"></a>ToggleHUD
Active ou désactive les diagnostics graphiques *HUD* (Head-Up Display) superposition ou désactiver.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Notes  
 Le HUD de diagnostics graphiques s’affiche dans le coin supérieur gauche de l’application qui s’exécute dans graphics diagnostics. Il affiche des informations d’exécution sur l’application et capture des informations graphiques, ainsi que les messages qui sont ajoutés en appelant le [AddMessage](addmessage.md) fonction membre.  
  
 Pour activer/désactiver le HUD, vous n’êtes pas obligé de capturer activement les informations graphiques, autrement dit, il peut être activé ou désactivé via une instance de la `VsgDbg` (classe), mais la [Init](init.md) fonction membre ne doit pas nécessairement être appelé en premier.