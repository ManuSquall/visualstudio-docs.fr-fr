---
title: 'Comment : déboguer en Mode mixte | Documents Microsoft'
ms.custom: ''
ms.date: 06/19/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09d18fec3e8d3830764846d1c25c9109b79b6fe4
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-debug-in-mixed-mode"></a>Comment : déboguer en mode mixte
Les procédures suivantes décrivent comment déboguer le code managé et le code natif, également connu sous le nom de débogage en mode mixte. Pour ce faire, il existe deux scénarios, selon si la DLL ou l'application est écrite en code natif :  
  
-   L'application appelante qui appelle votre DLL est écrite en code natif. Dans ce cas, votre DLL est managée et les débogueurs managés et natifs doivent être activés pour déboguer ces deux types de code. Vous pouvez le vérifier dans le  **\<projet > Pages de propriétés** boîte de dialogue. Tout dépend si vous avez démarré le débogage à partir du projet DLL ou du projet de l'application appelante.  
  
-   L'application appelante qui appelle votre DLL est écrite en code managé et votre DLL est écrite en code natif.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

Si vous n’avez pas accès au projet pour l’application appelante, vous pouvez déboguer une DLL à partir du projet DLL. Pour plus d'informations, consultez [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md). Vous n’avez pas besoin d’utiliser combiné pour déboguer uniquement le projet DLL.
  
### <a name="to-enable-mixed-mode-debugging-c-calling-app"></a>Pour activer le débogage en mode mixte (application appelante C++)  
  
1.  Dans **l’Explorateur de solutions**, sélectionnez le projet natif.
  
2.  Sur le **vue** menu, cliquez sur **Pages de propriétés**.
  
3.  Dans le  **\<projet > Pages de propriétés** boîte de dialogue, développez le **propriétés de Configuration** nœud et sélectionnez **débogage**.  
  
4.  Définissez **le Type de débogueur** à **mixte** ou **automatique**.

    ![Activer le débogage en mode mixte](../debugger/media/dbg-mixed-mode-from-native.png "activer le débogage en mode mixte")

### <a name="to-enable-mixed-mode-debugging-c-or-vb-calling-app"></a>Pour activer le débogage en mode mixte (application appelante de c# ou Visual Basic)  
  
1.  Dans **l’Explorateur de solutions**, sélectionnez le projet managé.  
  
2.  Sur le **vue** menu, cliquez sur **Pages de propriétés**.  
  
3.  Dans le  **\<projet > Pages de propriétés** boîte de dialogue, sélectionnez le **déboguer** onglet, puis sélectionnez **activer le débogage de code natif**

    ![Activer le débogage de code natif](../debugger/media/dbg-mixed-mode-from-csharp.png "activer le débogage de code natif")
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour déboguer à partir d’un projet DLL](../debugger/how-to-debug-from-a-dll-project.md)