---
title: 'Comment : spécifier des ensembles de règles de Code managé pour plusieurs projets dans une Solution | Microsoft Docs'
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
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 42b04eb88e6edee2d8250ac29a26f4cfe6562a29
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503622"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Comment : spécifier des ensembles de règles applicables au code managé pour plusieurs projets dans une solution
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : spécifier Managed Code ensembles de règles pour plusieurs projets dans une Solution](https://docs.microsoft.com/visualstudio/code-quality/how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution).  
  
Par défaut, tous les projets gérés d’une solution sont affectés à l’analyse du code règles minimales recommandées par Microsoft *ensemble de règles*. Vous pouvez modifier les ensembles de règles qui sont assignés aux projets d’une solution dans la boîte de dialogue Propriétés de la solution.  
  
> [!NOTE]
>  Par défaut, analyse de code de projet n’est pas exécuté comme une étape de génération. Pour activer l’analyse du code comme une étape de génération, consultez [Comment : configurer l’analyse du Code pour un projet de Code managé](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).  
  
### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Pour spécifier un ensemble de règles pour plusieurs projets dans une solution de code managé  
  
1.  Dans [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]. [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], ou [!INCLUDE[vsPro](../includes/vspro-md.md)] Ouvrez la solution.  
  
2.  Sur le **analyser** menu, cliquez sur **configurer l’analyse du Code pour la Solution**.  
  
3.  Si nécessaire, développez **propriétés communes**, puis cliquez sur **paramètres d’analyse de Code**.  
  
4.  Vous pouvez spécifier un ensemble de règles pour un ou plusieurs projets.  
  
    -   Pour spécifier un ensemble de règles pour un projet individuel, cliquez sur le nom du projet.  
  
    -   Pour spécifier un ensemble de règles pour plusieurs projets, maintenez la touche CTRL ENFONCÉE et cliquez sur les noms de projet.  
  
    -   Pour spécifier tous les projets dans la solution, maintenez la touche MAJ ENFONCÉE et cliquez sur dans la liste des projets.  
  
5.  Cliquez sur le **l’ensemble de règles** champ du projet et puis cliquez sur le nom de la règle défini que vous souhaitez appliquer.



