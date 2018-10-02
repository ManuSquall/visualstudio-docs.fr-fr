---
title: 'Comment : déboguer en Mode mixte | Microsoft Docs'
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
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ce056b60a3e080490a2ad60f4aee5a7b5c8dd63
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493960"
---
# <a name="how-to-debug-in-mixed-mode"></a>Comment : déboguer en mode mixte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : déboguer en Mode mixte](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-in-mixed-mode).  
  
Les procédures suivantes décrivent comment déboguer le code managé et le code natif, également connu sous le nom de débogage en mode mixte. Pour ce faire, il existe deux scénarios, selon si la DLL ou l'application est écrite en code natif :  
  
-   L'application appelante qui appelle votre DLL est écrite en code natif. Dans ce cas, votre DLL est managée et les débogueurs managés et natifs doivent être activés pour déboguer ces deux types de code. Vous pouvez le vérifier dans le  **\<projet > Pages de propriétés** boîte de dialogue. Tout dépend si vous avez démarré le débogage à partir du projet DLL ou du projet de l'application appelante.  
  
-   L'application appelante qui appelle votre DLL est écrite en code managé et votre DLL est écrite en code natif.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-mixed-mode-debugging"></a>Pour activer le débogage en mode mixte  
  
1.  Dans **l’Explorateur de solutions**, sélectionnez le projet.  
  
2.  Dans le menu **vue**, cliquez sur **Pages de propriétés**.  
  
3.  Dans le  **\<projet > Pages de propriétés** boîte de dialogue, développez le **propriétés de Configuration** nœud, puis sélectionnez **débogage**.  
  
4.  Définissez **Type de débogueur** à **mixte** ou **automatique**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour déboguer à partir d’un projet DLL](../debugger/how-to-debug-from-a-dll-project.md)



