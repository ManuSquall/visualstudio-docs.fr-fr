---
title: Code mixte & informations manquantes dans la fenêtre pile des appels
description: Dans les programmes en mode mixte (natif et managé), le débogueur ne peut pas toujours afficher la pile des appels complète. Découvrez les différences possibles lorsque le code natif appelle du code managé.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da8d3a469b957444935150f91567636aef0fb38a
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975262"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Code mixte et informations manquantes dans la fenêtre Pile des appels
En raison de différences entre la pile des appels du code managé et celle du code natif, le débogueur ne peut pas toujours afficher la pile des appels complète en cas de types de code mixtes. Quand du code natif appelle du code managé, vous pouvez noter les divergences suivantes dans la fenêtre **Pile des appels** :

- Le frame natif situé immédiatement au-dessus du code managé peut ne pas apparaître dans la fenêtre **Pile des appels**. Pour plus d’informations, consultez [Comment : effectuer un pas à pas sortant du code managé quand des frames natifs sont absents de la fenêtre pile des appels](how-to-use-the-call-stack-window.md).

- Pour les applications en mode mixte lancées en dehors du débogueur, la fenêtre **Pile des appels** peut n’afficher que le code managé et aucun des frames natifs ne sera visible.

  Ces deux situations sont assez rares. Dans la plupart des appels natifs au code managé, les piles d'appels apparaissent correctement.

## <a name="see-also"></a>Voir aussi
- [Comment : utiliser la fenêtre Pile des appels](../debugger/how-to-use-the-call-stack-window.md)