---
title: Options, Éditeur de texte, C/C++, Mise en forme
ms.date: 04/30/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- CPP
helpviewer_keywords:
- Text Editor Options dialog box, formatting
- ClangFormat
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 95683c93558f67457f0868a76f52d1334e7a6712
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817613"
---
# <a name="options-text-editor-cc-formatting"></a>Options, Éditeur de texte, C/C++, Mise en forme

Utilisez les pages de propriétés pour changer le comportement par défaut de l’Éditeur de code quand vous programmez en C ou C++.

![Pages de propriétés de mise en forme C++](media/cpp-formatting.png)

Pour accéder à cette page, dans la boîte de dialogue **Options**, dans le volet gauche, développez **Éditeur de texte**, développez **C/C++**, puis cliquez sur **Mise en forme**.

> [!NOTE]
> Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="general-page"></a>Page Général

Cette page propose des options pour mettre en forme des instructions et des blocs à mesure que vous les tapez.

::: moniker range="vs-2017"

**Visual Studio 2017 15.7 et versions ultérieures :**

::: moniker-end

la page comporte également des options pour la configuration de la prise en charge de [ClangFormat](https://clang.llvm.org/docs/ClangFormat.html) version 5.0. ClangFormat est un utilitaire qui simplifie l’application de style et de mise en forme à votre code en fonction d’un ensemble de règles qui peuvent être configurées dans un fichier .clang-format ou _clang-format.

### <a name="configuring-clangformat-options"></a>Configuration des options de ClangFormat

::: moniker range="vs-2017"

**Visual Studio 2017 15.7 et versions ultérieures :**

::: moniker-end

La prise en charge de ClangFormat est activée par défaut. Vous pouvez choisir parmi ces conventions de mise en forme courantes celles que vous souhaitez appliquer à tous vos projets : LLVM, Google, chrome, Mozilla ou WebKit. Vous pouvez également créer un fichier .clang-format ou _clang-format de définition de format personnalisé. Si un tel fichier est présent dans un dossier de projet, Visual Studio l’utilise pour mettre en forme tous les fichiers de code source dans ce dossier et ses sous-dossiers.

Par défaut, Visual Studio exécute clangformat.exe en arrière-plan et applique la mise en forme à mesure que vous tapez au clavier. Vous pouvez également faire en sorte de l’exécuter uniquement pour les commandes de mise en forme appelées manuellement **Mettre en forme le document (Ctrl+K, Ctrl+D)** ou **Mettre en forme la sélection (Ctrl+K, Ctrl+F)**.

## <a name="indentation-new-lines-spacing-wrapping-pages"></a>Pages Mise en retrait, Nouvelles lignes et Retour à la ligne

Ces pages permettent d’effectuer diverses personnalisations de mise en forme, mais elles sont ignorées si ClangFormat est activé.

## <a name="see-also"></a>Voir aussi

- [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)
- [Utilisation de la fonctionnalité IntelliSense](../../ide/using-intellisense.md)