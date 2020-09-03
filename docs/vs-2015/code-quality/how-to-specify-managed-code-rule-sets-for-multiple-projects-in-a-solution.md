---
title: 'Comment : spécifier des ensembles de règles de code managé pour plusieurs projets dans une solution | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.solution
ms.assetid: 92dc3250-a010-4396-b515-f03a0b30cd2a
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e5333f6133dd3fd56077c14d6e56cd6fdada4404
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656421"
---
# <a name="how-to-specify-managed-code-rule-sets-for-multiple-projects-in-a-solution"></a>Comment : spécifier des ensembles de règles applicables au code managé pour plusieurs projets dans une solution
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Par défaut, tous les projets managés d’une solution se voient affecter l' *ensemble*de règles d’analyse du code des règles minimales recommandées Microsoft. Vous pouvez modifier les ensembles de règles qui sont affectés aux projets d’une solution dans la boîte de dialogue Propriétés de la solution.

> [!NOTE]
> Par défaut, l’analyse du code du projet n’est pas exécutée comme une étape de génération. Pour activer l’analyse du code en tant qu’étape de génération, consultez [Comment : configurer l’analyse du code pour un projet de code managé](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

### <a name="to-specify-a-rule-set-for-multiple-projects-in-a-managed-code--solution"></a>Pour spécifier un ensemble de règles pour plusieurs projets dans une solution de code managé

1. Dans [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] . [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]ou [!INCLUDE[vsPro](../includes/vspro-md.md)] Ouvrez la solution.

2. Dans le menu **analyser** , cliquez sur **configurer l’analyse du code pour la solution**.

3. Si nécessaire, développez **Propriétés communes**, puis cliquez sur **paramètres d’analyse du code**.

4. Vous pouvez spécifier un ensemble de règles pour un ou plusieurs projets.

    - Pour spécifier un ensemble de règles pour un projet individuel, cliquez sur le nom du projet.

    - Pour spécifier un ensemble de règles pour plusieurs projets, maintenez la touche CTRL enfoncée et cliquez sur les noms de projet.

    - Pour spécifier tous les projets de la solution, maintenez la touche Maj enfoncée et cliquez dans la liste projet.

5. Cliquez sur le champ **ensemble de règles** d’un projet, puis cliquez sur le nom de l’ensemble de règles que vous souhaitez appliquer.
