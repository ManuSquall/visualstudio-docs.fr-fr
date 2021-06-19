---
title: Afficher la pile des appels dans le débogueur | Microsoft Docs
description: Utilisez la fenêtre pile des appels pour afficher les appels de fonction ou de procédure qui se trouvent actuellement sur la pile dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e905a509443cd5fd30e860a887dd895c5ee21a6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387474"
---
# <a name="view-the-call-stack-and-use-the-call-stack-window-in-the-debugger"></a>Afficher la pile des appels et utiliser la fenêtre pile des appels dans le débogueur

La fenêtre **Pile des appels** permet d’afficher les appels de fonctions ou de procédures actuellement dans la pile. La fenêtre **Pile des appels** montre l’ordre dans lequel les méthodes et les fonctions sont appelées. La pile des appels est un bon moyen d’examiner et de comprendre le flux d’exécution d’une application.

Lorsque les [symboles de débogage](#bkmk_symbols) ne sont pas disponibles pour une partie d’une pile des appels, la fenêtre **pile des appels** peut ne pas être en mesure d’afficher des informations correctes pour cette partie de la pile des appels, en affichant à la place :

`[Frames below may be incorrect and/or missing, no symbols loaded for name.dll]`

> [!NOTE]
> La fenêtre **Pile des appels** est similaire à la perspective Débogage dans certains IDE, comme Eclipse.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites ici, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, cliquez sur **Importation et exportation de paramètres** dans le menu **Outils**.  Consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

## <a name="view-the-call-stack-while-in-the-debugger"></a>Afficher la pile des appels dans le débogueur

- Pendant le débogage, dans le menu **Déboguer** , sélectionnez **Windows > pile des appels**.

  ![Fenêtre Pile des appels](../debugger/media/dbg_basics_callstack_window.png "CallStackWindow")

Une flèche jaune identifie le frame de pile où le pointeur d'exécution se trouve actuellement. Par défaut, les informations de ce frame de pile s’affichent dans les fenêtres source, **variables locales**, **automatique**, **Espion** et code **machine** . Pour modifier le contexte du débogueur en un autre Frame sur la pile, [basculez vers un autre frame de pile](#bkmk_switch).

## <a name="display-non-user-code-in-the-call-stack-window"></a>Afficher le code non-utilisateur dans la fenêtre pile des appels

- Cliquez avec le bouton droit sur la fenêtre **Pile des appels**, puis sélectionnez **Afficher le code externe**.

Le code non-utilisateur est un code qui n’est pas affiché lorsque [uniquement mon code](../debugger/just-my-code.md) est activé. En code managé, les frames de code non-utilisateur sont masqués par défaut. La notation suivante apparaît à la place des frames de code non-utilisateur :

`[<External Code>]`

## <a name="switch-to-another-stack-frame-change-the-debugger-context"></a><a name="bkmk_switch"></a> Basculer vers un autre frame de pile (modifier le contexte du débogueur)

1. Dans la fenêtre **pile des appels** , cliquez avec le bouton droit sur le frame de pile dont vous souhaitez afficher le code et les données.

    Ou vous pouvez double-cliquer sur un frame dans la fenêtre **pile des appels** pour basculer vers ce frame.

2. Sélectionnez **Basculer vers le frame**.

     Une flèche verte avec une queue d’extrémité s’affiche à côté du frame de pile sélectionné. Le pointeur d'exécution reste dans le frame d'origine, qui est toujours identifié par la flèche jaune. Si vous sélectionnez **Pas à pas** ou **Continuer** dans le menu **Déboguer**, l’exécution se poursuivra dans le frame d’origine, et non dans le frame sélectionné.

## <a name="view-the-source-code-for-a-function-on-the-call-stack"></a>Afficher le code source d’une fonction dans la pile des appels

- Dans la fenêtre **Pile des appels**, cliquez avec le bouton droit sur la fonction dont vous voulez afficher le code source, puis sélectionnez **Atteindre le code source**.

## <a name="run-to-a-specific-function-from-the-call-stack-window"></a>Exécuter jusqu’à une fonction spécifique de la fenêtre pile des appels

- Dans la fenêtre **pile des appels** , sélectionnez la fonction, cliquez avec le bouton droit, puis choisissez **Exécuter jusqu’au curseur**.

## <a name="set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Définir un point d’arrêt sur le point de sortie d’un appel de fonction

- Consultez [définir un point d’arrêt au niveau d’une fonction de pile des appels](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_from_debugger_windows).

## <a name="display-calls-to-or-from-another-thread"></a>Afficher les appels vers ou à partir d’un autre thread

- Cliquez avec le bouton droit sur la fenêtre **Pile des appels**, puis sélectionnez **Inclure les appels échangés avec d’autres threads**.

## <a name="visually-trace-the-call-stack"></a>Suivre visuellement la pile des appels

Dans Visual Studio Enterprise (uniquement), vous pouvez afficher les cartes de code pour la pile des appels pendant le débogage.

- Dans la fenêtre **Pile des appels**, ouvrez le menu contextuel. Choisissez **afficher la pile des appels sur la carte du code** (**CTRL**  +  **MAJ**  +  **`** ).

    Pour plus d’informations, consultez [mapper des méthodes sur la pile des appels pendant le débogage](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).

![Afficher la pile d’appels sur la carte du code](../debugger/media/dbg_basics_show_call_stack_on_code_map.gif "ShowCallStackOnCodeMap")

## <a name="view-the-disassembly-code-for-a-function-on-the-call-stack-c-c-visual-basic-f"></a>Afficher le code machine d’une fonction dans la pile des appels (C#, C++, Visual Basic, F #)

- Dans la fenêtre **Pile des appels**, cliquez avec le bouton droit sur la fonction dont vous voulez afficher le code machine, puis sélectionnez **Atteindre le code machine**.

## <a name="change-the-optional-information-displayed"></a>Modifier les informations facultatives affichées

- Cliquez avec le bouton droit dans la fenêtre **pile des appels** et définissez ou désélectionnez **afficher \<**_the information that you want_**>**.

## <a name="load-symbols-for-a-module-c-c-visual-basic-f"></a><a name="bkmk_symbols"></a> Charger des symboles pour un module (C#, C++, Visual Basic, F #)

Dans la fenêtre **Pile des appels**, vous pouvez charger des symboles de débogage pour du code qui ne possède actuellement aucun symbole chargé. Ces symboles peuvent être des symboles .NET ou système téléchargés à partir des serveurs de symboles publics Microsoft, ou des symboles dans un chemin d’accès aux symboles sur l’ordinateur que vous déboguez.

Consultez [spécifier les fichiers de symboles (. pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

### <a name="to-load-symbols"></a>Pour charger des symboles

1. Dans la fenêtre **pile des appels** , cliquez avec le bouton droit sur le frame de pile pour lequel les symboles ne sont pas chargés. La frame est alors grisée.

2. Pointez sur **charger les symboles** , puis sélectionnez serveurs de **symboles Microsoft** (si disponibles) ou recherchez le chemin d’accès aux symboles.

### <a name="to-set-the-symbol-path"></a>Pour définir le chemin d'accès aux symboles

1. Dans la fenêtre **Pile des appels**, choisissez **Paramètres des symboles** dans le menu contextuel.

     La boîte de dialogue **Options** s’ouvre et la page **Symboles** s’affiche.

2. Sélectionnez **paramètres des symboles**.

3. Dans la boîte de dialogue **Options**, cliquez sur l’icône de dossier.

     Un curseur apparaît dans la zone **Emplacements du fichier de symboles (.pdb)**.

4. Entrez un chemin d’accès au répertoire de l’emplacement des symboles sur l’ordinateur que vous déboguez. Pour le débogage local et distant, il s’agit d’un chemin d’accès sur votre ordinateur local.

5. Sélectionnez **OK** pour fermer la boîte de dialogue **options** .

## <a name="see-also"></a>Voir aussi

- [Code mixte et informations manquantes dans la fenêtre Pile des appels](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)
- [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)
- [Spécifier les fichiers de symboles (. pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Utilisation des points d'arrêt](../debugger/using-breakpoints.md)