---
title: 'Comment : supprimer les avertissements d’analyse de Code pour le Code généré | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 07858183af427e2b67e1e0f63d1f8889caf72fbe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49293740"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Comment : supprimer les avertissements d'analyse du code pour du code généré
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les compilateurs de code managé génèrent souvent un code qui est ajouté à un projet pour faciliter le développement de code rapide. En outre, les développeurs utilisent souvent des outils tiers pour aider à développer rapidement des applications. Ces outils génèrent également le code qui est ajouté au projet.  
  
 Vous souhaiterez peut-être consulter les violations de règle que l’analyse du Code détecte dans le code généré. Toutefois, vous souhaiterez pas les voir si vous ne peut pas afficher et gérer le code qui contient la violation.  
  
 Le **supprimer les résultats du code généré** case à cocher sur la page de propriétés de l’analyse du Code d’un projet vous permet de choisir si vous souhaitez afficher les avertissements d’analyse du Code à partir du code généré par un outil tiers.  
  
> [!NOTE]
>  Cette option ne supprime pas les erreurs d’analyse du Code et les avertissements du code généré lorsque les erreurs et avertissements s’affichent dans les formulaires et les modèles. Vous pouvez afficher et gérer le code source pour un formulaire ou un modèle.  
  
### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Pour supprimer des avertissements pour du code généré dans un projet  
  
1.  Cliquez sur le projet dans l’Explorateur de solutions, puis cliquez sur **propriétés**.  
  
2.  Cliquez sur **analyse du Code**.  
  
3.  Sélectionnez le **supprimer les résultats du code généré** case à cocher.



