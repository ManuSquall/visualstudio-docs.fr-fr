---
title: 'Procédure : Spécifier des ensembles de règles de Code managé pour plusieurs projets dans une Solution | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2bf83c66f86d516d18221d01470e125979d39349
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939235"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Procédure : Spécifier des ensembles de règles de Code managé pour plusieurs projets dans une Solution
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Par défaut, tous les projets gérés d’une solution sont affectés à l’analyse du code règles minimales recommandées par Microsoft *ensemble de règles*. Vous pouvez modifier les ensembles de règles qui sont assignés aux projets d’une solution dans la boîte de dialogue Propriétés de la solution.  
  
> [!NOTE]
>  Par défaut, analyse de code de projet n’est pas exécuté comme une étape de génération. Pour activer l’analyse du code comme une étape de génération, consultez [Comment : Configurer l’analyse du Code pour un projet de Code managé](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).  
  
### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Pour spécifier un ensemble de règles pour plusieurs projets dans une solution de code managé  
  
1.  Dans [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], ou [!INCLUDE[vsPro](../includes/vspro-md.md)] Ouvrez la solution.  
  
2.  Sur le **analyser** menu, cliquez sur **configurer l’analyse du Code pour la Solution**.  
  
3.  Si nécessaire, développez **propriétés communes**, puis cliquez sur **paramètres d’analyse de Code**.  
  
4.  Vous pouvez spécifier un ensemble de règles pour un ou plusieurs projets.  
  
    -   Pour spécifier un ensemble de règles pour un projet individuel, cliquez sur le nom du projet.  
  
    -   Pour spécifier un ensemble de règles pour plusieurs projets, maintenez la touche CTRL ENFONCÉE et cliquez sur les noms de projet.  
  
    -   Pour spécifier tous les projets dans la solution, maintenez la touche MAJ ENFONCÉE et cliquez sur dans la liste des projets.  
  
5.  Cliquez sur le **l’ensemble de règles** champ du projet et puis cliquez sur le nom de la règle défini que vous souhaitez appliquer.
