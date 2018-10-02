---
title: 'Comment : supprimer les avertissements d’analyse de Code pour le Code généré | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 81bb371a3e16236e22ab3a1fd4ac5ab431f61512
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495721"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Comment : supprimer les avertissements d'analyse du code pour du code généré
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : supprimer des avertissements d’analyse de Code pour le Code généré](https://docs.microsoft.com/visualstudio/code-quality/how-to-suppress-code-analysis-warnings-for-generated-code).  
  
Les compilateurs de code managé génèrent souvent un code qui est ajouté à un projet pour faciliter le développement de code rapide. En outre, les développeurs utilisent souvent des outils tiers pour aider à développer rapidement des applications. Ces outils génèrent également le code qui est ajouté au projet.  
  
 Vous souhaiterez peut-être consulter les violations de règle que l’analyse du Code détecte dans le code généré. Toutefois, vous souhaiterez pas les voir si vous ne peut pas afficher et gérer le code qui contient la violation.  
  
 Le **supprimer les résultats du code généré** case à cocher sur la page de propriétés de l’analyse du Code d’un projet vous permet de choisir si vous souhaitez afficher les avertissements d’analyse du Code à partir du code généré par un outil tiers.  
  
> [!NOTE]
>  Cette option ne supprime pas les erreurs d’analyse du Code et les avertissements du code généré lorsque les erreurs et avertissements s’affichent dans les formulaires et les modèles. Vous pouvez afficher et gérer le code source pour un formulaire ou un modèle.  
  
### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Pour supprimer des avertissements pour du code généré dans un projet  
  
1.  Cliquez sur le projet dans l’Explorateur de solutions, puis cliquez sur **propriétés**.  
  
2.  Cliquez sur **analyse du Code**.  
  
3.  Sélectionnez le **supprimer les résultats du code généré** case à cocher.



