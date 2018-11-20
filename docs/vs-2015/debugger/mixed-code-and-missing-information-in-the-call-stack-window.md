---
title: Code mixte et informations manquantes dans la fenêtre Pile des appels | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 6f4ae8e527e5f6ce04680c444baad58802bfad48
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788928"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Code mixte et informations manquantes dans la fenêtre Pile des appels
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En raison de différences entre la pile des appels du code managé et celle du code natif, le débogueur ne peut pas toujours afficher la pile des appels complète en cas de types de code mixtes. Lorsque le code natif appelle du code managé, vous pouvez noter les divergences suivantes dans le **pile des appels** fenêtre :  
  
- Le frame natif immédiatement au-dessus du code managé peut-être être absent dans les **pile des appels** fenêtre. Pour plus d’informations, consultez [Comment : sortir du Code managé lorsque les Frames natifs sont absents de la fenêtre Pile des appels](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
- Pour les applications en mode mixte lancées en dehors du débogueur, le **pile des appels** fenêtre peut afficher uniquement le code managé et aucun des frames natifs ne sera visible.  
  
  Ces deux situations sont assez rares. Dans la plupart des appels natifs au code managé, les piles d'appels apparaissent correctement.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour utiliser la fenêtre Pile des appels](../debugger/how-to-use-the-call-stack-window.md)





