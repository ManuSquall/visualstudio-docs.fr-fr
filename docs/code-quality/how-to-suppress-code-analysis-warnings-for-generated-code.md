---
title: "Comment : supprimer les avertissements d’analyse du Code pour le Code généré | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 24b94c0c4ce6031876f5ad26ce01a22299f7056a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Comment : supprimer les avertissements d'analyse du code pour du code généré
Les compilateurs de code managé génèrent souvent un code qui est ajouté à un projet pour faciliter le développement de code rapide. En outre, les développeurs utilisent souvent des outils tiers pour aider à développer rapidement des applications. Ces outils génèrent également un code qui est ajouté au projet.  
  
 Vous pouvez souhaiter consulter les violations de règle que l’analyse du Code découvre dans le code généré. Toutefois, vous pouvez les visualiser, si vous ne peut pas afficher et gérer le code qui contient la violation.  
  
 Le **supprimer les résultats du code généré** case à cocher sur la page de propriétés de l’analyse du Code d’un projet vous permet de choisir si vous souhaitez consulter les avertissements d’analyse du Code à partir du code généré par un outil tiers.  
  
> [!NOTE]
>  Cette option ne supprime pas les erreurs d’analyse du Code et les avertissements du code généré lorsque les erreurs et avertissements s’affichent dans les formulaires et les modèles. Vous pouvez afficher et gérer le code source pour un formulaire ou un modèle.  
  
### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Supprimer les avertissements pour du code généré dans un projet  
  
1.  Cliquez sur le projet dans l’Explorateur de solutions, puis cliquez sur **propriétés**.  
  
2.  Cliquez sur **l’analyse du Code**.  
  
3.  Sélectionnez le **supprimer les résultats du code généré** case à cocher.