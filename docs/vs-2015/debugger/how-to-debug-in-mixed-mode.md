---
title: 'Procédure : Déboguer en Mode mixte | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e4a20faa34e8d0dd1018cb4cb5ee0a6df098177
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60107188"
---
# <a name="how-to-debug-in-mixed-mode"></a>Procédure : Déboguer en Mode mixte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les procédures suivantes décrivent comment déboguer le code managé et le code natif, également connu sous le nom de débogage en mode mixte. Pour ce faire, il existe deux scénarios, selon si la DLL ou l'application est écrite en code natif :  
  
- L'application appelante qui appelle votre DLL est écrite en code natif. Dans ce cas, votre DLL est managée et les débogueurs managés et natifs doivent être activés pour déboguer ces deux types de code. Vous pouvez le vérifier dans le  **\<projet > Pages de propriétés** boîte de dialogue. Tout dépend si vous avez démarré le débogage à partir du projet DLL ou du projet de l'application appelante.  
  
- L'application appelante qui appelle votre DLL est écrite en code managé et votre DLL est écrite en code natif.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-mixed-mode-debugging"></a>Pour activer le débogage en mode mixte  
  
1. Dans **l’Explorateur de solutions**, sélectionnez le projet.  
  
2. Dans le menu **vue**, cliquez sur **Pages de propriétés**.  
  
3. Dans le  **\<projet > Pages de propriétés** boîte de dialogue, développez le **propriétés de Configuration** nœud, puis sélectionnez **débogage**.  
  
4. Définissez **Type de débogueur** sur **Mixte** ou **Automatique**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour déboguer à partir d’un projet DLL](../debugger/how-to-debug-from-a-dll-project.md)
