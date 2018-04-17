---
title: 'Comment : pas à pas sortant du Code managé lorsque les Frames natifs sont absents de la fenêtre Pile des appels | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5c64016f5ca0613a2986ec8a0bf305d88ecffd64
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Comment : effectuer un pas à pas sortant du code managé lorsque les frames natifs sont absents de la fenêtre Pile des appels
Si votre code intègre des frames natifs invisibles dans la **pile des appels** fenêtre, pas à pas sortant du code managé peut produire des résultats inattendus. Pour résoudre ce problème, vous pouvez utiliser un point d’arrêt au lieu de **pas à pas sortant**.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Pour sortir pas à pas du code managé lorsque les frames natifs n'apparaissent pas dans la fenêtre Pile des appels  
  
1.  Dans le code natif, définissez un point d'arrêt d'emplacement après l'appel de code managé.  
  
2.  Sur le **déboguer** menu, choisissez **continuer**.  
  
     Une fois que l'appel de code managé sera terminé, l'exécution s'arrêtera au point d'arrêt dans le code natif.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour utiliser la fenêtre Pile des appels](../debugger/how-to-use-the-call-stack-window.md)