---
title: Afficher les dll et les exécutables
description: Affichez les dll et les exécutables (fichiers .exe) que votre application utilise dans la fenêtre modules pendant une session de débogage dans Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: Visual Studio Modules window
ms.date: 11/04/2018
ms.topic: how-to
f1_keywords:
- vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f82b8a5051cf1c338c4b1aab6e78209fb2bc08b0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385407"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>Afficher les dll et les exécutables dans la fenêtre modules (C#, C++, Visual Basic, F #)

Lors du débogage de Visual Studio, la fenêtre **modules** répertorie et affiche des informations sur les dll et les fichiers exécutables (fichiers *.exe* ) utilisés par votre application.

> [!NOTE]
> La fenêtre modules n’est pas disponible pour le débogage SQL ou de script.

## <a name="use-the-modules-window"></a>Utiliser la fenêtre Modules

Pour ouvrir la fenêtre modules pendant le débogage, sélectionnez **Déboguer** les  >    >  **modules** Windows (ou appuyez sur **Ctrl + Alt + U**).

Par défaut, la fenêtre **Modules** trie les modules dans l’ordre de chargement. Pour trier selon une colonne de la fenêtre, sélectionnez l’en-tête en haut de la colonne.

## <a name="load-symbols"></a>Charger les symboles

La colonne **État du symbole** dans la fenêtre **modules** indique les modules dont les symboles de débogage sont chargés. Si l’État est **ignoré lors du chargement des symboles**, si vous **ne parvenez pas à trouver ou à ouvrir le fichier PDB** ou à charger le **paramètre inclure/exclure**, vous pouvez charger les symboles manuellement. Pour plus d’informations sur le chargement et l’utilisation de symboles, consultez [spécifier les fichiers de symboles (. pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

**Pour charger les symboles manuellement :**

1. Dans la fenêtre **modules** , cliquez avec le bouton droit sur le module pour lequel les symboles n’ont pas été chargés.

   - Sélectionnez **informations** sur le chargement des symboles pour plus d’informations sur la raison pour laquelle les symboles n’ont pas été chargés.

   - Sélectionnez **charger les symboles** pour charger les symboles manuellement.

1. Si les symboles ne se chargent pas, sélectionnez **paramètres des symboles** pour ouvrir la boîte de dialogue **options** , puis spécifiez ou modifiez les emplacements de chargement des symboles.

   Vous pouvez télécharger des symboles à partir des serveurs de symboles publics Microsoft ou d’autres serveurs, ou charger des symboles à partir d’un dossier sur votre ordinateur. Pour plus d’informations, consultez [spécifier les emplacements de symboles et le comportement de chargement](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).

**Pour modifier les paramètres de comportement du chargement des symboles :**

1. Dans la fenêtre **Modules**, cliquez avec le bouton droit sur un module.

1. Sélectionnez **paramètres des symboles**.

1. Sélectionnez **charger tous les symboles** ou sélectionnez les modules à inclure ou à exclure.

1. Sélectionnez **OK**. Les modifications prennent effet lors de la prochaine session de débogage.

**Pour modifier le comportement de chargement des symboles pour un module spécifique :**

1. Dans la fenêtre **Modules**, cliquez avec le bouton droit sur le module.

1. Dans le menu contextuel, sélectionnez ou désélectionnez **toujours charger automatiquement**. Les modifications prennent effet lors de la prochaine session de débogage.

## <a name="see-also"></a>Voir aussi
- [Interruption de l’exécution](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))
- [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)
- [Spécifier les fichiers de symboles (. pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)