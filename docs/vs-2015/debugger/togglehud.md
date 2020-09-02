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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144574"
---
# <a name="togglehud"></a>ToggleHUD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Active ou désactive la superposition de Graphics Diagnostics *HUD* (affichage de tête haut).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Notes  
 Le HUD Graphics Diagnostics s’affiche dans l’angle supérieur gauche de l’application exécutée dans Graphics Diagnostics. Il affiche des informations d’exécution sur l’application et sur la capture des informations graphiques, ainsi que des messages ajoutés en appelant la fonction membre [AddMessage](../debugger/addmessage.md) .  
  
 Pour activer/désactiver le HUD, vous n’êtes pas obligé de capturer activement les informations graphiques, c’est-à-dire qu’elles peuvent être basculées par le biais d’une instance de la `VsgDbg` classe, mais la fonction membre [init](../debugger/init.md) n’a pas besoin d’être appelée en premier.
