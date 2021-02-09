---
title: ToggleHUD | Microsoft Docs
description: Utilisez la méthode ToggleHUD () de Vsgdbg, pour basculer entre l’affichage de l’affichage en tête de Graphics Diagnostics (HUD) lors de l’exécution de l’application.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6cde6549551156f3655f313c23dc66659d2830cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905053"
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