---
title: Options, Éditeur de texte, JavaScript, Linting
ms.date: 1/15/2019
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Linting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Linting
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Linting.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Linting
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9c62970ab6377ddaaf295007fd49ba8be7dd225
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026280"
---
# <a name="options-text-editor-javascript-linting"></a>Options, Éditeur de texte, JavaScript, Linting

Utilisez la page **Linting** de la boîte de dialogue **Options** pour définir les options d’analyse du code dans l’éditeur de code. Pour accéder à cette page, dans la barre de menus, choisissez **Outils** > **Options**, puis développez **Éditeur de texte** > **JavaScript** > **Linting**.

## <a name="eslint-settings"></a>Paramètres d’ESLint

Ces options vous permettent d’activer l’analyse statique du code JavaScript et choisir quels fichiers sont analysés. Pour plus d’informations sur ESLint, consultez [ESLint.org](https://eslint.org/).

### <a name="uielement-list"></a>Liste UIElement

|Option|Description|
|------------|-----------------|
|**Activer ESLint**|Quand cette option est sélectionnée, l’éditeur de code autorise l’analyse statique du code.|
|**Effectuer une validation Lint sur tous les fichiers inclus dans le projet, même les fichiers fermés**|Quand cette option est sélectionnée, les fichiers fermés sont analysés, sauf si les diagnostics sont signalés uniquement pour les fichiers ouverts.|

## <a name="global-eslint-config-options"></a>Options de configuration ESLint globales

Cette option vous permet de copier l’emplacement du fichier de configuration ESLint global. En outre, si vous avez changé l’emplacement, vous pouvez réinitialiser le fichier à son emplacement par défaut.

## <a name="see-also"></a>Voir aussi

- [Général, Environnement, boîte de dialogue Options](../../ide/reference/general-environment-options-dialog-box.md)