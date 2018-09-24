---
title: Afficher la pile des appels dans le débogueur Visual Studio | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 04/06/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 168f89512dee8331448db1becabdc7262b5e4744
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43774727"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-visual-studio-debugger"></a>Afficher la pile des appels et utiliser la fenêtre Pile des appels dans le débogueur Visual Studio

À l’aide de la **pile des appels** , vous pouvez afficher les appels de fonction ou une procédure qui se trouvent actuellement sur la pile. Le **pile des appels** fenêtre indique l’ordre dans lequel les méthodes et les fonctions sont bien appelées. La pile des appels est un bon moyen d’examiner et de comprendre le flux d’exécution d’une application.
  
Lorsque [symboles de débogage](#bkmk_symbols) ne sont pas disponibles pour une partie d’une pile des appels, le **pile des appels** fenêtre ne peut pas être en mesure d’afficher des informations correctes pour cette partie de la pile des appels. Si cela se produit, la notation suivante apparaît :  
  
`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

>  [!NOTE]
> Le **pile des appels** est identique à la perspective de débogage dans certains IDE comme Eclipse. 

> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites ici, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, sélectionnez **importation et exportation de paramètres** sur le **outils** menu.  Consultez [personnalisation de l’IDE](../ide/personalizing-the-visual-studio-ide.md)
  
## <a name="view-the-call-stack-while-in-the-debugger"></a>Afficher la pile des appels dans le débogueur 
  
-   Pendant le débogage, dans le **déboguer** menu, sélectionnez **Windows > pile des appels**.

 ![Fenêtre Pile des appels](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Une flèche jaune identifie le frame de pile où le pointeur d'exécution se trouve actuellement. Par défaut, il s’agit du frame de pile dont les informations apparaissent dans la source, **variables locales**, **automatique**, **espion**, et **désassemblage** windows . Si vous souhaitez modifier le contexte du débogueur vers un autre frame sur la pile, vous pouvez le faire [basculer vers un autre frame de pile](#bkmk_switch).   
  
## <a name="display-non-user-code-in-the-call-stack-window"></a>Afficher le code non-utilisateur dans la fenêtre Pile des appels  
  
-   Cliquez sur le **pile des appels** fenêtre et sélectionnez **afficher le Code externe**.

Code non-utilisateur est un code qui n’est pas affiché quand [uniquement mon Code](../debugger/just-my-code.md) est activé. Dans le code managé, les frames de code non-utilisateur sont masqués par défaut. La notation suivante apparaît au lieu des frames de code non-utilisateur :  
  
**[\<Code externe >]**  
  
## <a name="bkmk_switch"></a> Basculer vers un autre frame de pile (modifier le contexte du débogueur)
  
1.  Dans le **pile des appels** fenêtre, clic droit de la pile de frame dont code et les données que vous souhaitez afficher.

    Ou, vous pouvez double-cliquer sur un frame dans la **pile des appels** fenêtre pour basculer vers le frame sélectionné. 
  
2.  Sélectionnez **basculer vers le Frame**.  
  
     Une flèche verte avec extrémité recourbée apparaît à côté du frame de pile que vous avez sélectionné. Le pointeur d'exécution reste dans le frame d'origine, qui est toujours identifié par la flèche jaune. Si vous sélectionnez **étape** ou **continuer** à partir de la **déboguer** menu, l’exécution se poursuivra dans le frame d’origine, pas dans le frame sélectionné.  
  
## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Afficher le code source pour une fonction sur la pile des appels  
  
-   Dans le **pile des appels** fenêtre, clic droit de la fonction dont la source code que vous souhaitez afficher et sélectionner **atteindre le Code Source**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Exécuter jusqu'à une fonction spécifique à partir de la fenêtre Pile des appels  
  
-  Dans le **pile des appels** fenêtre, sélectionnez la fonction, avec le bouton droit et choisissez **exécuter jusqu’au curseur**.  
  
## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Définir un point d’arrêt sur le point de sortie d’un appel de fonction  
  
-   Consultez [définir un point d’arrêt à une fonction de pile d’appel](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).

## <a name="display-calls-to-or-from-another-thread"></a>Afficher les appels vers ou à partir d’un autre thread  
  
-   Cliquez sur le **pile des appels** fenêtre et sélectionnez **inclure les appels échangés avec d’autres Threads**.   
  
## <a name="visually-trace-the-call-stack"></a>Afficher la trace de la pile des appels  

Si vous utilisez Visual Studio Enterprise (uniquement), vous pouvez afficher des cartes de code pour la pile des appels pendant le débogage.

- Dans le **pile des appels** fenêtre, ouvrez le menu contextuel. Choisissez **afficher la pile des appels sur carte de Code**. (Clavier : **CTRL** + **MAJ** + **`**)  
  
    Pour plus d’informations, consultez [mapper les méthodes sur la pile des appels pendant le débogage](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Afficher la pile des appels sur carte de Code](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")
  
## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack"></a>Afficher le code machine pour une fonction sur la pile des appels  
  
-   Dans le **pile des appels** fenêtre, clic droit de la fonction dont le code machine code que vous souhaitez afficher et sélectionner **atteindre le code machine**.    

## <a name="change-the-optional-information-displayed"></a>Modifier l’affichage des informations facultatives  
  
-   Cliquez sur le **pile des appels** fenêtre et activez ou désactivez **afficher \<**  _les informations que vous souhaitez_ **>**.  
  
## <a name="bkmk_symbols"></a> Charger les symboles pour un module
Dans le **pile des appels** fenêtre, vous pouvez charger des symboles de débogage pour le code qui n’a pas de symboles chargés. Ces symboles peuvent être des symboles .NET Framework ou système téléchargés à partir des serveurs de symboles publics de Microsoft ou des symboles situés dans un chemin d’accès aux symboles sur l’ordinateur que vous déboguez.  
  
Consultez [spécifier les symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
### <a name="to-load-symbols"></a>Pour charger des symboles  
  
1.  Dans le **pile des appels** fenêtre, avec le bouton droit du frame de pile pour lequel des symboles ne sont pas chargés. La frame est alors grisée.  
  
2.  Pointez sur **charger les symboles** puis cliquez sur **serveurs de symboles Microsoft** (si disponible) ou recherchez le chemin d’accès du symbole.  
  
### <a name="to-set-the-symbol-path"></a>Pour définir le chemin d’accès aux symboles  
  
1.  Dans le **pile des appels** fenêtre, choisissez **paramètres des symboles** dans le menu contextuel.  
  
     Le **Options** boîte de dialogue s’ouvre et la **symboles** page s’affiche.  
  
2.  Cliquez sur **paramètres des symboles**.  
  
3.  Dans le **Options** boîte de dialogue, cliquez sur l’icône de dossier.  
  
     Dans le **emplacements du fichier (.pdb) de symboles** zone, un curseur s’affiche.  
  
4.  Tapez un chemin d’accès au répertoire correspondant à l’emplacement de symboles sur l’ordinateur que vous déboguez. Pour le débogage local et distant, il s’agit d’un chemin d’accès sur votre ordinateur local.
  
5.  Cliquez sur **OK** pour fermer la boîte de dialogue **Options**.  
  
## <a name="see-also"></a>Voir aussi  
 [Code mixte et informations manquantes dans la fenêtre Pile des appels](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)  
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)   
 [Spécifier les symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Utilisation des points d’arrêt](../debugger/using-breakpoints.md)