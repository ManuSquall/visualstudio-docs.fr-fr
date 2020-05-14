---
title: Options, Éditeur de texte, JavaScript, Projet
ms.date: 1/15/2019
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 190cbdb2a8096415985d83fc525b997572d252c2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68605931"
---
# <a name="options-text-editor-javascript-project"></a>Options, Éditeur de texte, JavaScript, Projet

Utilisez la page **Projet** de la boîte de dialogue **Options** pour spécifier les options de projet JavaScript et TypeScript dans l’éditeur de code. Pour accéder à cette page, sur la barre de menu, choisissez **Tools** > **Options**, puis développez **Text Editor** > **JavaScript/TypeScript** > **Project**.

## <a name="project-analysis-options"></a>Options d’analyse du projet

Ces options déterminent comment l’éditeur analyse les projets, signale les diagnostics et suggère des améliorations. Activez ou désactivez les options pour spécifier la façon dont l’éditeur gère ces situations.

### <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

- **Analyser uniquement les projets contenant des fichiers ouverts dans l’éditeur**
- **Signaler uniquement les diagnostics des fichiers ouverts dans l’éditeur**
- **Suggérer des améliorations possibles qui ne sont pas des corrections**

## <a name="virtual-projects-in-solution-explorer"></a>Projets virtuels dans l’Explorateur de solutions

Ces options vous permettent de choisir s’il faut afficher les projets virtuels quand une solution est chargée ou non chargée.

## <a name="compile-on-save"></a>Compiler lors de l’enregistrement

Ces options déterminent si les fichiers TypeScript qui ne font pas partie du projet sont compilés automatiquement. Cochez la case, puis choisissez le type de génération de code à utiliser.

### <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

- **Utiliser la génération de code AMD pour les modules qui ne font pas partie d’un projet**
- **Utiliser la génération de code CommonJS pour les modules qui ne font pas partie d’un projet**
- **Utiliser la génération de code UMD pour les modules qui ne font pas partie d’un projet**
- **Utiliser la génération de code système pour les modules qui ne font pas partie d’un projet**
- **Utiliser la génération de code ES2015 pour les modules qui ne font pas partie d’un projet**

## <a name="ecmascript-version-for-files-that-are-not-part-of-a-project"></a>Version ECMAScript des fichiers qui ne font pas partie d’un projet

Ces options vous permet de sélectionner la version ECMAScript des fichiers qui ne font pas partie d’un projet. Vous pouvez choisir **ECMAScript 3**, **ECMAScript 5** ou **ECMAScript 6**.

## <a name="jsx-emit-for-tsx-files-that-are-not-part-of-a-project"></a>Émission JSX pour des fichiers TSX qui ne font pas partie d’un projet

Ces options déterminent comment l’éditeur traite les fichiers TypeScript qui ne font pas partie d’un projet.

### <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

|Option|Description|
|------------|-----------------|
|**Infrastructure React**|Quand cette option est sélectionnée, l’éditeur de code émet une extension de fichier *.js*.|
|**Préserver**|Quand cette option est sélectionnée, l’éditeur de code conserve le JSX en tant que partie de la sortie et émet une extension de fichier *.jsx*.|

## <a name="see-also"></a>Voir aussi

- [Général, Environnement, Options Dialog Box](../../ide/reference/general-environment-options-dialog-box.md)