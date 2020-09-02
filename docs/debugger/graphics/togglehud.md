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
ms.openlocfilehash: cb05bb6a424b5639e0ee98e96c80315c51081ace
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62848477"
---
# <a name="togglehud"></a>ToggleHUD
Active ou désactive la superposition de Graphics Diagnostics *HUD* (affichage de tête haut).

## <a name="syntax"></a>Syntaxe

```C++
void ToggleHUD();
```

## <a name="remarks"></a>Notes
 Le HUD Graphics Diagnostics s’affiche dans l’angle supérieur gauche de l’application exécutée dans Graphics Diagnostics. Il affiche des informations d’exécution sur l’application et sur la capture des informations graphiques, ainsi que des messages ajoutés en appelant la fonction membre [AddMessage](addmessage.md) .

 Pour activer/désactiver le HUD, vous n’êtes pas obligé de capturer activement les informations graphiques, c’est-à-dire qu’elles peuvent être basculées par le biais d’une instance de la `VsgDbg` classe, mais la fonction membre [init](init.md) n’a pas besoin d’être appelée en premier.