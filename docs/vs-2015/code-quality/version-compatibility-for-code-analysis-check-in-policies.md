---
title: Compatibilité des versions pour les stratégies d’archivage de l’analyse du Code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0a63ead03baffaa0ce8047220ff1ce8a33c88be8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201153"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Compatibilité des versions des stratégies d'archivage de l'analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous devez évaluer et créer des stratégies analyse du code de vérification à l’aide de différentes versions de [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], vous devez connaître les différences dans la manière dont [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] et [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] évaluer les stratégies d’archivage.  
  
## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilité des versions d’évaluation des stratégies d’archivage  
  
- Lorsque les stratégies d’archivage de l’analyse du code sont évalués dans [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], toutes les règles qui existaient dans [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] mais n’existent pas dans [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] sont ignorés.  
  
- Lorsque les stratégies d’archivage de l’analyse du code sont évalués dans [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], toutes les nouvelles règles qui sont exclusives à [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] sont ignorés.  
  
- Si la stratégie d’archivage de l’analyse du code spécifie des assemblys de règles, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] ignore toutes les règles qui sont spécifiées par les assemblys qu’il ne reconnaît pas.  
  
- Si la stratégie d’archivage de l’analyse du code spécifie des assemblys de règles qui [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] ne reconnaît pas, un message s’affiche.  
  
## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilité des versions pour la création de stratégies d’archivage  
  
- Si vous avez créé une stratégie d’archivage de l’analyse du code à l’aide de la [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] version de [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], vous ne pouvez pas utiliser le [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] version de [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] pour le modifier. Et également, [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] ne peut pas évaluer la stratégie.  
  
- Si vous avez créé une stratégie d’archivage de l’analyse du code à l’aide de [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] dans [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], vous pouvez utiliser [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] dans [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] pour modifier la stratégie et peut également être évalué que par [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]. Après avoir modifié la stratégie à l’aide de [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] dans [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], vous ne pouvez plus modifier la stratégie à l’aide de [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] dans [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]. [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] évaluer les stratégies sans problème avec des noms forts ne correspondent pas.  
  
- Pour créer une stratégie d’archivage de l’analyse du code avec des paramètres de règle qui s’appliquent à la fois pour [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] et [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], vous devez créer la stratégie dans [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], apportez toutes les modifications nécessaires et enregistrer la stratégie. Si les modifications apportées aux règles existent uniquement dans [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], vous modifiez et enregistrez la stratégie dans [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)].  
  
     Après avoir enregistré la stratégie dans [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], vous ne pouvez plus modifier les paramètres des règles qui existent dans [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] uniquement.
