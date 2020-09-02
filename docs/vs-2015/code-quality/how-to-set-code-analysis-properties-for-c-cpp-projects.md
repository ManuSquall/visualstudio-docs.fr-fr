---
title: 'Comment : définir les propriétés d’analyse du code pour les projets C-C++ | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: b2fb3cb81b49fd4b8cc83e0548110d2025c7488d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277984"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Comment : définir les propriétés d'analyse du code pour les projets C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez configurer les règles que l’outil d’analyse du code utilise pour analyser le code de chaque configuration de votre projet. En outre, vous pouvez diriger l’analyse du code pour supprimer les avertissements du code qui a été généré et ajouté à votre projet par un outil tiers.  
  
## <a name="code-analysis-property-page"></a>Page de propriétés de l’analyse du code  
 La page de propriétés **analyse du code** contient tous les paramètres de configuration de l’analyse du code pour un projet. Pour ouvrir la page de propriétés analyse du code pour un projet dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**. Ensuite, développez **Propriétés de configuration** et sélectionnez l’onglet **analyse du code** .  
  
## <a name="project-configuration-and-platform"></a>Configuration du projet et plateforme  
 La liste de **configurations** et la liste de **plateformes** vous permettent d’appliquer différents paramètres d’analyse du code à différentes configurations de projet et combinaisons de plateformes. Par exemple, vous pouvez diriger l’analyse du code pour appliquer un ensemble de règles à votre projet pour les versions de débogage et un autre ensemble pour les versions release.  
  
## <a name="enabling-code-analysis"></a>Activation de l’analyse du code  
 Vous pouvez décider d’activer ou non l’analyse du code pour votre projet en sélectionnant **activer l’analyse du code pour C/C++ sur la build**. En association avec la liste de **configuration** , vous pouvez, par exemple, décider de désactiver l’analyse du code pour les builds de débogage et de l’activer pour les versions release.  
  
 Si votre projet contient du code managé, vous pouvez décider s’il faut activer ou désactiver l’analyse du code en sélectionnant **activer l’analyse du code sur la build**.  
  
 L’analyse du code est conçue pour vous aider à améliorer la qualité de votre code et à éviter les pièges les plus courants. Par conséquent, Déterminez soigneusement s’il faut désactiver l’analyse du code. Il est généralement préférable de désactiver les ensembles de règles ou les règles individuelles que vous ne souhaitez pas appliquer à votre projet.  
  
## <a name="generated-code"></a>Code généré  
 Les développeurs utilisent fréquemment des outils pour développer rapidement des applications. Ces outils peuvent générer du code qui est ajouté au projet. Vous pouvez consulter les violations de règle découvertes par l’analyse du code dans le code généré. Toutefois, vous ne voudrez peut-être pas les afficher si vous ne souhaitez pas conserver le code.  
  
 La case à cocher **Supprimer les résultats du code généré** sur la page Propriétés **générales** vous permet de choisir si vous souhaitez afficher des avertissements d’analyse du code managé générés par un outil tiers.  
  
## <a name="rule-sets"></a>Ensembles de règles  
 Si votre projet contient du code managé, vous pouvez sélectionner les règles à appliquer dans une analyse du code en sélectionnant un ensemble de règles dans la liste **exécuter cet ensemble de règles** .  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de la qualité du code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Analyse du code pour les avertissements C/C++](../code-quality/code-analysis-for-c-cpp-warnings.md)
