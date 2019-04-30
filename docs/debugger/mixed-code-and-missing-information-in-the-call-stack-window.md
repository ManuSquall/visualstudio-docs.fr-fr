---
title: Code mixte et informations manquantes dans la fenêtre Pile des appels | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 025591ffea4d6746f87e5f1240cd226fa291d116
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905507"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Code mixte et informations manquantes dans la fenêtre Pile des appels
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En raison de différences entre la pile des appels du code managé et celle du code natif, le débogueur ne peut pas toujours afficher la pile des appels complète en cas de types de code mixtes. Quand du code natif appelle du code managé, vous pouvez noter les divergences suivantes dans la fenêtre **Pile des appels** :  
  
- Le frame natif situé immédiatement au-dessus du code managé peut ne pas apparaître dans la fenêtre **Pile des appels**. Pour plus d'informations, voir [Procédure : Pas à pas sortant du code managé quand des images natives manquent dans la fenêtre Pile des appels](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
- Pour les applications en mode mixte lancées en dehors du débogueur, la fenêtre **Pile des appels** peut n’afficher que le code managé et aucun des frames natifs ne sera visible.  
  
  Ces deux situations sont assez rares. Dans la plupart des appels natifs au code managé, les piles d'appels apparaissent correctement.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour utiliser la fenêtre Pile des appels](../debugger/how-to-use-the-call-stack-window.md)
