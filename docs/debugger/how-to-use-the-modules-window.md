---
title: Afficher les DLL et les exécutables
titleSuffix: Visual Studio Modules window
ms.custom: seodec18
ms.date: 11/04/2018
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 400961eaa14b87d70a685a87be5df48ac92c8281
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62906140"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>Afficher les DLL et les exécutables dans la fenêtre Modules (C#, C++, Visual Basic, F#)

Pendant le débogage de Visual Studio, le **Modules** fenêtre répertorie et affiche des informations sur les DLL et les fichiers exécutables (*.exe* fichiers) utilise votre application.

> [!NOTE]
> La fenêtre Modules n’est pas disponible pour le débogage de script ou SQL.

## <a name="use-the-modules-window"></a>Utiliser la fenêtre Modules

Pour ouvrir la fenêtre Modules, pendant que vous déboguez, sélectionnez **déboguer** > **Windows** > **Modules** (ou appuyez sur **Ctrl + Alt + U** ).

Par défaut, la fenêtre **Modules** trie les modules dans l’ordre de chargement. Pour trier par n’importe quelle colonne de la fenêtre, sélectionnez l’en-tête en haut de la colonne.

## <a name="load-symbols"></a>Charger les symboles

Le **état du symbole** colonne dans le **Modules** fenêtre montre quels modules ont chargé des symboles de débogage. Si l’état est **chargement des symboles ignoré**, **ne peut pas trouver ou ouvrir le fichier PDB**, ou **chargement désactivé par le paramètre include/exclude**, vous pouvez charger manuellement les symboles. Pour plus d’informations sur le chargement et l’utilisation de symboles, consultez [spécifier les symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

**Pour charger des symboles manuellement :**

1. Dans le **Modules** fenêtre, avec le bouton droit, le module pour lequel des symboles n’est pas chargé.

   - Sélectionnez **charger les informations de symboles** pour plus d’informations sur la raison n’a pas charger les symboles.

   - Sélectionnez **charger les symboles** pour charger manuellement les symboles.

1. Si les symboles ne se chargent pas, sélectionnez **paramètres des symboles** pour ouvrir le **Options** boîte de dialogue et spécifier ou modifier des emplacements le chargement des symboles.

   Vous pouvez télécharger des symboles à partir des serveurs de symboles publics de Microsoft ou d’autres serveurs ou charger des symboles à partir d’un dossier sur votre ordinateur. Pour plus d’informations, consultez [spécifier des emplacements de symboles et le comportement de chargement](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).

**Pour modifier les paramètres de comportement de chargement des symboles :**

1. Dans la fenêtre **Modules**, cliquez avec le bouton droit sur un module.

1. Sélectionnez **paramètres des symboles**.

1. Sélectionnez **charger tous les symboles**, ou sélectionnez les modules à inclure ou exclure.

1. Sélectionnez **OK**. Modifications prennent effet dans la prochaine session de débogage.

**Pour modifier le comportement d’un module spécifique de chargement de symboles :**

1. Dans la fenêtre **Modules**, cliquez avec le bouton droit sur le module.

1. Dans le menu contextuel, sélectionnez ou désélectionnez **charge automatiquement**. Modifications prennent effet dans la prochaine session de débogage.

## <a name="see-also"></a>Voir aussi
- [Interruption de l’exécution](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))
- [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)
- [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)