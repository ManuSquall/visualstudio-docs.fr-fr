---
title: "Comment : définir les propriétés d’analyse de Code pour les projets C/C++ | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b2ad22eccb561bf58ee845d58268620aad778a20
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Comment : définir les propriétés d'analyse du code pour les projets C/C++
Vous pouvez configurer les règles utilisées par l’outil d’analyse du code pour analyser le code dans chaque configuration de votre projet. En outre, vous pouvez diriger l’analyse du code pour supprimer les avertissements du code qui a été généré et ajouté à votre projet par un outil tiers.  
  
## <a name="code-analysis-property-page"></a>Page de propriété d’analyse du code  
 Le **l’analyse du Code** page de propriétés contient tous les paramètres de configuration de l’analyse du code pour un projet. Pour ouvrir la page propriété analyse du code pour un projet dans **l’Explorateur de solutions**, cliquez sur le projet, puis sur **propriétés**. Développez ensuite **propriétés de Configuration** et sélectionnez le **l’analyse du Code** onglet.  
  
## <a name="project-configuration-and-platform"></a>Plateforme et Configuration de projet  
 Le **Configuration** liste et **plateforme** liste vous permet d’appliquer les paramètres d’analyse de code différentes à des combinaisons de configuration et la plateforme de projet différent. Par exemple, vous pouvez diriger les versions de l’analyse du code pour appliquer un ensemble de règles à votre projet pour le débogage et un ensemble différent de version les versions.  
  
## <a name="enabling-code-analysis"></a>L’activation de l’analyse du Code  
 Vous pouvez décider s’il faut activer l’analyse du code pour votre projet en sélectionnant **activer Code Analysis pour C/C++ sur la Build**. En association avec le **Configuration** la liste, vous pouvez, par exemple, décider de désactiver l’analyse du Code pour les versions debug et activer pour cette version de génération.  
  
 Si votre projet contient du code managé, vous pouvez décider s’il faut activer ou désactiver l’analyse du Code en sélectionnant **activer l’analyse du Code sur la Build**.  
  
 Analyse du code est conçue pour vous aider à améliorer la qualité de votre code et éviter les pièges courants. Par conséquent, réfléchissez bien avant de s’il faut désactiver l’analyse du code. Il est généralement préférable de désactiver les ensembles de règles ou des règles individuelles que vous ne voulez pas appliquées à votre projet.  
  
## <a name="generated-code"></a>Code généré  
 Les développeurs utilisent fréquemment des outils pour développer rapidement des applications. Ces outils peuvent générer le code qui est ajouté au projet. Vous pouvez souhaiter consulter les violations de règle que l’analyse du code découvre dans le code généré. Toutefois, vous pouvez les voir si vous ne souhaitez pas mettre à jour le code.  
  
 Le **supprimer les résultats du Code généré** case à cocher sur la **général** page de propriétés vous permet d’indiquer si vous souhaitez afficher les avertissements d’analyse du code managé qui est généré par un outil tiers .  
  
## <a name="rule-sets"></a>Ensembles de règles  
 Si votre projet contient du code managé, vous pouvez sélectionner les règles à appliquer dans une analyse du code en sélectionnant un ensemble de règles la **exécuter cet ensemble de règles** liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de la qualité du Code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Avertissements liés à l’analyse de code C/C++](../code-quality/code-analysis-for-c-cpp-warnings.md)