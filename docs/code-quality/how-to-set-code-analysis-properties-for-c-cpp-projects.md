---
title: "Comment : définir les propriétés d'analyse du code pour les projets C/C++"
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 27f3d68d28b8d1799c52fcf83c6a00dc5f81f48a
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448920"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Comment : définir les propriétés d'analyse du code pour les projets C/C++

Vous pouvez configurer les règles que l’outil d’analyse du code utilise pour analyser le code de chaque configuration de votre projet. En outre, vous pouvez diriger l’analyse du code pour supprimer les avertissements du code qui a été généré et ajouté à votre projet par un outil tiers.

## <a name="code-analysis-property-page"></a>Page de propriétés de l’analyse du code

La page de propriétés **analyse du code** contient tous les paramètres de configuration de l’analyse du code pour un projet MSBuild. Pour ouvrir la page de propriétés analyse du code pour un projet dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**. Ensuite, développez **Propriétés de configuration** et sélectionnez l’onglet **analyse du code** .

## <a name="project-configuration-and-platform"></a>Configuration du projet et plateforme

La liste de la liste et de la **plateforme** de **configuration** située en haut de la fenêtre vous permet d’appliquer différents paramètres d’analyse du code à différentes configurations de projet et combinaisons de plateformes. Par exemple, vous pouvez diriger l’analyse du code pour appliquer un ensemble de règles à votre projet pour les versions de débogage et un autre ensemble pour les versions release.

## <a name="enabling-code-analysis"></a>Activation de l’analyse du code

Vous pouvez activer l’analyse du code pour votre projet en basculant sur les options **activer l’analyse du code Microsoft** et **activer Clang-Tidy** , et configurer plus précisément s’il s’exécute sur la build en sélectionnant **activer l’analyse du code lors de la génération**. En association avec la liste de **configuration** , vous pouvez, par exemple, décider de désactiver l’analyse du code pour les builds de débogage et de l’activer pour les versions release.

L’analyse du code est conçue pour vous aider à améliorer la qualité de votre code et à éviter les pièges les plus courants. Par conséquent, Déterminez soigneusement s’il faut désactiver l’analyse du code. Il est généralement préférable de désactiver les ensembles de règles, les règles individuelles ou les vérifications individuelles que vous ne souhaitez pas appliquer à votre projet.

## <a name="cmake-configuration"></a>Configuration de CMake

Dans les projets CMake, modifiez la valeur des clés `enableMicrosoftCodeAnalysis` et `enableClangTidyCodeAnalysis` dans `CMakeSettings.json` pour activer ou désactiver l’analyse du code. Pour plus d’informations, consultez [utilisation de Clang-Tidy dans Visual Studio](../code-quality/clang-tidy.md) .

## <a name="see-also"></a>Voir aussi

- [Analyse de la qualité d’un code managé](../code-quality/code-analysis-for-managed-code-overview.md)
- [Avertissements liés à l’analyse de code C/C++](../code-quality/code-analysis-for-c-cpp-warnings.md)
- [Ensembles de règles C++ pour le code](../code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run.md)
- [Utilisation de Clang-Tidy](../code-quality/clang-tidy.md)
