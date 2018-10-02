---
title: 'Comment : sortir du Code managé lorsque les Frames natifs sont absents de la fenêtre Pile des appels | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 682d4f9c8973f8deee65efa0cd8c0d78061ee00a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494211"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Comment : effectuer un pas à pas sortant du code managé lorsque les frames natifs sont absents de la fenêtre Pile des appels
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : sortir du Code managé lorsque les Frames natifs sont absents de la fenêtre Pile des appels](https://docs.microsoft.com/visualstudio/debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window).  
  
Si votre code intègre des frames natifs invisibles dans le **pile des appels** fenêtre, pas à pas sortant du code managé peut produire des résultats inattendus. Pour résoudre ce problème, vous pouvez utiliser un point d’arrêt au lieu de **pas à pas sortant**.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Pour sortir pas à pas du code managé lorsque les frames natifs n'apparaissent pas dans la fenêtre Pile des appels  
  
1.  Dans le code natif, définissez un point d'arrêt d'emplacement après l'appel de code managé.  
  
2.  Sur le **déboguer** menu, choisissez **continuer**.  
  
     Une fois que l'appel de code managé sera terminé, l'exécution s'arrêtera au point d'arrêt dans le code natif.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour utiliser la fenêtre Pile des appels](../debugger/how-to-use-the-call-stack-window.md)





