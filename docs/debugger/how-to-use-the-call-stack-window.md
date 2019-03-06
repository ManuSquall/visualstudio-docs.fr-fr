---
title: Afficher la pile des appels dans le débogueur | Microsoft Docs
ms.custom: seodec18
ms.date: 10/29/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58b8e9bc37cde33a09a06503755f2646cca6f75c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018798"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>Afficher la pile des appels et utiliser la fenêtre Pile des appels dans le débogueur

La fenêtre **Pile des appels** permet d’afficher les appels de fonctions ou de procédures actuellement dans la pile. La fenêtre **Pile des appels** montre l’ordre dans lequel les méthodes et les fonctions sont appelées. La pile des appels est un bon moyen d’examiner et de comprendre le flux d’exécution d’une application.

Lorsque [symboles de débogage](#bkmk_symbols) ne sont pas disponibles pour une partie d’une pile des appels, le **pile des appels** fenêtre n’est peut-être pas en mesure d’afficher des informations correctes pour cette partie de la pile des appels, afficher à la place :

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> La fenêtre **Pile des appels** est similaire à la perspective Débogage dans certains IDE, comme Eclipse.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites ici, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, cliquez sur **Importation et exportation de paramètres** dans le menu **Outils**.  Consultez [réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

## <a name="view-the-call-stack-while-in-the-debugger"></a>Afficher la pile des appels dans le débogueur

- Pendant le débogage, dans le **déboguer** menu, sélectionnez **Windows > pile des appels**.

  ![Fenêtre Pile des appels](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Une flèche jaune identifie le frame de pile où le pointeur d'exécution se trouve actuellement. Par défaut, les informations de ce frame de pile apparaissent dans la source, **variables locales**, **automatique**, **espion**, et **désassemblage** windows. Pour modifier le contexte du débogueur vers un autre frame sur la pile, [basculer vers un autre frame de pile](#bkmk_switch).

## <a name="display-non-user-code-in-the-call-stack-window"></a>Afficher le code non-utilisateur dans la fenêtre Pile des appels

-   Cliquez avec le bouton droit sur la fenêtre **Pile des appels**, puis sélectionnez **Afficher le code externe**.

Code non-utilisateur est un code qui n’est pas affiché quand [uniquement mon Code](../debugger/just-my-code.md) est activé. Dans le code managé, les frames de code non-utilisateur sont masqués par défaut. La notation suivante apparaît à la place les frames de code non-utilisateur :

`[<External Code>]`

## <a name="bkmk_switch"></a> Basculer vers un autre frame de pile (modifier le contexte du débogueur)

1.  Dans le **pile des appels** fenêtre, clic droit de la pile de frame dont code et les données que vous souhaitez afficher.

    Ou, vous pouvez double-cliquer sur un frame dans la **pile des appels** fenêtre pour basculer vers ce frame.

2.  Sélectionnez **Basculer vers le frame**.

     Une flèche verte avec extrémité recourbée apparaît à côté du frame de pile que vous avez sélectionné. Le pointeur d'exécution reste dans le frame d'origine, qui est toujours identifié par la flèche jaune. Si vous sélectionnez **Pas à pas** ou **Continuer** dans le menu **Déboguer**, l’exécution se poursuivra dans le frame d’origine, et non dans le frame sélectionné.

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Afficher le code source pour une fonction sur la pile des appels

-   Dans la fenêtre **Pile des appels**, cliquez avec le bouton droit sur la fonction dont vous voulez afficher le code source, puis sélectionnez **Atteindre le code source**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Exécuter jusqu'à une fonction spécifique à partir de la fenêtre Pile des appels

-  Dans le **pile des appels** fenêtre, sélectionnez la fonction, avec le bouton droit, puis choisissez **exécuter jusqu’au curseur**.

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Définir un point d’arrêt sur le point de sortie d’un appel de fonction

-   Consultez [définir un point d’arrêt à une fonction de pile d’appel](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).

## <a name="display-calls-to-or-from-another-thread"></a>Afficher les appels vers ou à partir d’un autre thread

-   Cliquez avec le bouton droit sur la fenêtre **Pile des appels**, puis sélectionnez **Inclure les appels échangés avec d’autres threads**.

## <a name="visually-trace-the-call-stack"></a>Afficher la trace de la pile des appels

Dans Visual Studio Enterprise (uniquement), vous pouvez afficher des cartes de code pour la pile des appels pendant le débogage.

- Dans la fenêtre **Pile des appels**, ouvrez le menu contextuel. Choisissez **afficher la pile des appels sur carte de Code** (**Ctrl** + **MAJ** + **`**).

    Pour plus d’informations, consultez [mapper les méthodes sur la pile des appels pendant le débogage](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Afficher la pile des appels sur carte de Code](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Afficher le code machine pour une fonction sur la pile des appels (C#, C++, Visual Basic, F#)

-   Dans la fenêtre **Pile des appels**, cliquez avec le bouton droit sur la fonction dont vous voulez afficher le code machine, puis sélectionnez **Atteindre le code machine**.

## <a name="change-the-optional-information-displayed"></a>Modifier l’affichage des informations facultatives

-   Avec le bouton droit dans le **pile des appels** fenêtre et activez ou désactivez **afficher \<**  _les informations que vous souhaitez_ **>**.

## <a name="bkmk_symbols"></a> Charger les symboles pour un module (C#, C++, Visual Basic, F#)

Dans la fenêtre **Pile des appels**, vous pouvez charger des symboles de débogage pour du code qui ne possède actuellement aucun symbole chargé. Ces symboles peuvent être des symboles .NET Framework ou système téléchargés à partir des serveurs de symboles publics de Microsoft ou des symboles situés dans un chemin d’accès aux symboles sur l’ordinateur que vous déboguez.

Consultez [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-load-symbols"></a>Pour charger des symboles

1.  Dans le **pile des appels** fenêtre, avec le bouton droit du frame de pile pour lequel des symboles ne sont pas chargés. La frame est alors grisée.

2.  Pointez sur **charger les symboles** , puis sélectionnez **serveurs de symboles Microsoft** (si disponible), ou recherchez le chemin d’accès du symbole.

### <a name="to-set-the-symbol-path"></a>Pour définir le chemin d’accès aux symboles

1.  Dans la fenêtre **Pile des appels**, choisissez **Paramètres des symboles** dans le menu contextuel.

     La boîte de dialogue **Options** s’ouvre et la page **Symboles** s’affiche.

2.  Sélectionnez **paramètres des symboles**.

3.  Dans la boîte de dialogue **Options**, cliquez sur l’icône de dossier.

     Un curseur apparaît dans la zone **Emplacements du fichier de symboles (.pdb)**.

4.  Entrez un chemin d’accès du répertoire à l’emplacement de symboles sur l’ordinateur que vous déboguez. Pour le débogage local et distant, il s’agit d’un chemin d’accès sur votre ordinateur local.

5.  Sélectionnez **OK** pour fermer la **Options** boîte de dialogue.

## <a name="see-also"></a>Voir aussi

- [Code mixte et informations manquantes dans la fenêtre Pile des appels](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)
- [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Utilisation des points d’arrêt](../debugger/using-breakpoints.md)