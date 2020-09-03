---
title: Compatibilité des versions pour les stratégies d’archivage de l’analyse du code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 075981569cbee05e90afe17b3afc9558d7bbb270
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609317"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Compatibilité des versions des stratégies d'archivage de l'analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous devez évaluer et créer des stratégies d’archivage de l’analyse du code à l’aide de différentes versions de [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] , vous devez connaître les différences dans la façon dont [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] et [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] évaluer les stratégies d’archivage.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilité des versions pour l’évaluation des stratégies d’archivage

- Lorsque les stratégies d’archivage de l’analyse du code sont évaluées dans [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , toutes les règles qui existaient dans [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] mais n’existent pas dans [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] sont ignorées.

- Lorsque les stratégies d’archivage de l’analyse du code sont évaluées dans [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , toutes les nouvelles règles qui sont exclusives à [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] sont ignorées.

- Si la stratégie d’archivage de l’analyse du code spécifie des assemblys de règles, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] ignore toutes les règles qui sont spécifiées par les assemblys qu’il ne reconnaît pas.

- Si la stratégie d’archivage de l’analyse du code spécifie des assemblys de règles qui [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] ne sont pas reconnus, un message s’affiche.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilité des versions pour la création de stratégies d’archivage

- Si vous avez créé une stratégie d’archivage de l’analyse du code à l’aide [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] de la version de [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] , vous ne pouvez pas utiliser la [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] version de [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] pour la modifier. En outre, [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] ne peut pas évaluer la stratégie.

- Si vous avez créé une stratégie d’archivage de l’analyse du code à l’aide [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] de dans [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , vous pouvez utiliser [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] dans [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] pour la modifier, et la stratégie peut également être évaluée par [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] . Après avoir modifié la stratégie à l’aide [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] de dans [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , vous ne pouvez plus modifier la stratégie à l’aide [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] de dans [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] . [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] peut évaluer les stratégies sans problèmes avec des noms forts incompatibles.

- Pour créer une stratégie d’archivage de l’analyse du code avec des paramètres de règle qui s’appliquent à la fois à [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] et [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , vous devez créer la stratégie dans [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , apporter toutes les modifications nécessaires et enregistrer la stratégie. Si les modifications apportées aux règles existent uniquement dans [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , vous modifiez et enregistrez la stratégie dans [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] .

     Une fois que vous avez enregistré la stratégie dans [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , vous ne pouvez plus modifier les paramètres des règles qui existent dans [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] uniquement.
