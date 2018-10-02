---
title: 'Comment : définir les propriétés d’analyse de Code pour les projets C / C++ | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
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
caps.latest.revision: 19
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2c0b396394e003f97c60a65ee37b94810e692e28
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503492"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Comment : définir les propriétés d'analyse du code pour les projets C/C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : définir des propriétés d’analyse de Code pour les projets C/C++](https://docs.microsoft.com/visualstudio/code-quality/how-to-set-code-analysis-properties-for-c-cpp-projects).  
  
Vous pouvez configurer les règles utilisées par l’outil d’analyse de code pour analyser le code dans chaque configuration de votre projet. En outre, vous pouvez diriger l’analyse du code pour supprimer des avertissements à partir du code qui a été généré et ajouté à votre projet par un outil tiers.  
  
## <a name="code-analysis-property-page"></a>Propriété Page analyse du code  
 Le **analyse du Code** page de propriétés contient tous les paramètres de configuration de l’analyse du code pour un projet. Pour ouvrir la page propriété analyse du code pour un projet dans **l’Explorateur de solutions**, cliquez sur le projet, puis cliquez sur **propriétés**. Ensuite, développez **propriétés de Configuration** et sélectionnez le **analyse du Code** onglet.  
  
## <a name="project-configuration-and-platform"></a>Plateforme et Configuration de projet  
 Le **Configuration** liste et **plateforme** liste vous permet d’appliquer les paramètres d’analyse de code différents à des combinaisons de configuration et la plateforme de projet différent. Par exemple, vous pouvez diriger les builds de l’analyse du code pour appliquer un ensemble de règles à votre projet pour le débogage et génère un ensemble différent de version.  
  
## <a name="enabling-code-analysis"></a>L’activation de l’analyse du Code  
 Vous pouvez décider s’il faut activer l’analyse du code pour votre projet en sélectionnant **activer Code Analysis pour C/C++ sur la Build**. En association avec le **Configuration** liste, vous pouvez, par exemple, décider de désactiver l’analyse du Code pour les versions debug et activer les versions release.  
  
 Si votre projet contient du code managé, vous pouvez décider s’il faut activer ou désactiver l’analyse du Code en sélectionnant **activer l’analyse du Code sur la Build**.  
  
 Analyse du code est conçue pour vous aider à améliorer la qualité de votre code et éviter les pièges courants. Par conséquent, réfléchissez bien s’il faut désactiver l’analyse du code. Il est généralement préférable de désactiver les ensembles de règles ou des règles individuelles que vous ne souhaitez pas appliqués à votre projet.  
  
## <a name="generated-code"></a>Code généré  
 Les développeurs utilisent fréquemment des outils pour vous aider à développer rapidement des applications. Ces outils peuvent générer du code qui est ajouté au projet. Vous souhaiterez peut-être consulter les violations de règle que l’analyse du code détecte dans le code généré. Toutefois, vous souhaiterez pas les voir si vous ne souhaitez pas gérer le code.  
  
 Le **supprimer les résultats du Code généré** case à cocher sur la **général** vous permet de sélectionner si vous souhaitez afficher les avertissements d’analyse du code managé qui est généré par un outil tiers de page de propriétés .  
  
## <a name="rule-sets"></a>Ensembles de règles  
 Si votre projet contient du code managé, vous pouvez sélectionner les règles à appliquer dans une analyse du code en sélectionnant un ensemble de règles la **exécuter cet ensemble de règles** liste.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse de la qualité d’un code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Avertissements liés à l’analyse de code C/C++](../code-quality/code-analysis-for-c-cpp-warnings.md)



