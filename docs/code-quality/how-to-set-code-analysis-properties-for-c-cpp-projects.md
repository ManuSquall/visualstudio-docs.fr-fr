---
title: "Comment&#160;: d&#233;finir les propri&#233;t&#233;s d&#39;analyse du code pour les projets C/C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.native"
  - "VC.Project.VCCLCompilerTool.EnablePrefast"
  - "VC.Project.VCFxCopTool.EnablePREfast"
  - "VC.Project.VCFxCopTool.IgnoreGeneratedCode"
helpviewer_keywords: 
  - "analyse du code C/C++ (propriétés)"
  - "propriétés de l'analyse du code"
  - "propriétés, analyse du code C/C++"
  - "propriétés, analyse du code"
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Comment&#160;: d&#233;finir les propri&#233;t&#233;s d&#39;analyse du code pour les projets C/C++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez configurer les règles utilisées par l'outil d'analyse du code pour analyser le code dans chaque configuration de votre projet.  De plus, vous pouvez donner l'ordre à l'analyse du code de supprimer les avertissements d'un code généré et ajouté à votre projet par un outil tiers.  
  
## Page de propriétés Analyse du code  
 La page de propriétés **Analyse du code** contient tous les paramètres de configuration de l'analyse du code pour un projet.  Pour ouvrir la page de propriétés Analyse du code d'un projet dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet et cliquez sur **Propriétés**.  Ensuite, développez **Propriétés de configuration** et sélectionnez l'onglet **Analyse du code**.  
  
## Plateforme et configuration de projet  
 Les listes **Configuration** et **Plateforme** vous permettent d'appliquer différents paramètres d'analyse du code à différentes combinaisons de plateforme et de configuration de projet.  Par exemple, vous pouvez donner l'ordre à l'analyse du code d'appliquer un ensemble de règles à votre projet pour les versions  Debug et un ensemble différent pour les versions Release.  
  
## Activation de l'analyse du code  
 Vous pouvez choisir d'activer l'analyse du code pour votre projet en sélectionnant  **Activer l'analyse du code pour la génération C\/C\+\+**.  À l'aide de la liste **Configuration**, vous pouvez, par exemple, décider de désactiver l'analyse du code pour les versions Debug et de l'activer pour les versions Release.  
  
 Si votre projet contient du code managé, vous pouvez choisir d'activer ou de désactiver l'analyse du code en sélectionnant **Activer l'analyse du code lors de la build**.  
  
 L'analyse du code est conçue pour vous aider à améliorer la qualité de votre code et à éviter les pièges courants.  Par conséquent, considérez attentivement s'il convient ou non de la désactiver.  De manière générale, il vaut mieux désactiver les ensembles de règles ou les règles particulières que vous ne souhaitez pas appliquer à votre projet.  
  
## Code généré  
 Les développeurs utilisent souvent des outils afin de développer rapidement des applications.  Ces outils génèrent également un code qui est ajouté au projet.  Il est recommandé de consulter les violations de règle que l'analyse du code découvre dans le code généré.  Toutefois, il ne vous est peut\-être pas utile de les consulter si vous ne souhaitez pas maintenir le code.  
  
 La case à cocher **Supprimer les résultats du code généré** sur la page de propriétés **Générales** vous permet de choisir si vous souhaitez ou non consulter les avertissements d'analyse du code managé qui est généré par un outil tiers.  
  
## Ensembles de règles  
 Si votre projet contient du code managé, vous pouvez sélectionner les règles à appliquer dans une analyse du code en choisissant un ensemble de règles dans la liste **Exécuter cet ensemble de règles**.  
  
## Voir aussi  
 [Analyse de la qualité d’un code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Analyse de code pour les avertissements C\/C\+\+](../code-quality/code-analysis-for-c-cpp-warnings.md)