---
title: ToggleHUD | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02b461ac8d80146bc86bf3636a367900fcdb8f39
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51786936"
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



