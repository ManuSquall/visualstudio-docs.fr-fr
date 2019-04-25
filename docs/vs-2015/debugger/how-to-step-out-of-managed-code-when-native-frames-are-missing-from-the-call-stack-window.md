---
title: 'Procédure : Sortir du Code managé lorsque les Frames natifs sont absents de la fenêtre Pile des appels | Microsoft Docs'
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
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 684738fd2180a3c5bf269b2a30efd970bcf9ab08
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092199"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Procédure : Pas à pas sortant du code managé quand des images natives manquent dans la fenêtre Pile des appels
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si votre code intègre des frames natifs invisibles dans la fenêtre **Pile des appels**, une sortie pas à pas du code managé peut produire des résultats inattendus. Pour éviter cela, vous pouvez utiliser un point d’arrêt plutôt qu’un **Pas à pas sortant**.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Pour sortir pas à pas du code managé lorsque les frames natifs n'apparaissent pas dans la fenêtre Pile des appels  
  
1. Dans le code natif, définissez un point d'arrêt d'emplacement après l'appel de code managé.  
  
2. Dans le menu **Déboguer**, sélectionnez **Continuer**.  
  
     Une fois que l'appel de code managé sera terminé, l'exécution s'arrêtera au point d'arrêt dans le code natif.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour utiliser la fenêtre Pile des appels](../debugger/how-to-use-the-call-stack-window.md)
