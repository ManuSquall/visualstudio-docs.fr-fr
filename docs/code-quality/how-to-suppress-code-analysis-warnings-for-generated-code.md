---
title: 'Comment : supprimer les avertissements d’analyse du Code pour le Code généré | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a44dae0dce544a4783be3068cbd52d7b9825e4bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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