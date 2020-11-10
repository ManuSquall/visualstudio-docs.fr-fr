---
title: Compatibilité des versions des stratégies d'archivage de l'analyse du code
ms.date: 11/04/2016
description: Découvrez comment Team System 2008 Team Foundation Server et Team Foundation Server 2010 évaluer les stratégies d’archivage de Visual Studio différemment.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a681f510da270bc22ae4bc983103f9a5735a127
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436873"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Compatibilité des versions des stratégies d'archivage de l'analyse du code

Si vous devez évaluer et créer des stratégies d’archivage de l’analyse du code à l’aide de différentes versions de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] , vous devez connaître les différences dans la façon dont [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] et [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] évaluer les stratégies d’archivage.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilité des versions pour l’évaluation des stratégies de Check-In

- Lorsque les stratégies d’archivage de l’analyse du code sont évaluées dans [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , toutes les règles qui existaient dans [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] mais n’existent pas dans [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] sont ignorées.

- Lorsque les stratégies d’archivage de l’analyse du code sont évaluées dans [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , toutes les nouvelles règles qui sont exclusives à [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] sont ignorées.

- Si la stratégie d’archivage de l’analyse du code spécifie des assemblys de règles, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignore toutes les règles qui sont spécifiées par les assemblys qu’il ne reconnaît pas.

- Si la stratégie d’archivage de l’analyse du code spécifie des assemblys de règles qui [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ne sont pas reconnus, un message s’affiche.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilité des versions pour la création de stratégies de Check-In

- Si vous avez créé une stratégie d’archivage de l’analyse du code à l’aide [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] de la version de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] , vous ne pouvez pas utiliser la [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] version de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] pour la modifier. En outre, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ne peut pas évaluer la stratégie.

- Si vous avez créé une stratégie d’archivage de l’analyse du code à l’aide [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] de dans [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , vous pouvez utiliser [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] dans [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] pour la modifier, et la stratégie peut également être évaluée par [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] . Après avoir modifié la stratégie à l’aide [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] de dans [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , vous ne pouvez plus modifier la stratégie à l’aide [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] de dans [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] . [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] peut évaluer les stratégies sans problèmes avec des noms forts incompatibles.

- Pour créer une stratégie d’archivage de l’analyse du code avec des paramètres de règle qui s’appliquent à la fois à [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] et [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , vous devez créer la stratégie dans [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , apporter toutes les modifications nécessaires et enregistrer la stratégie. Si les modifications apportées aux règles existent uniquement dans [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , vous modifiez et enregistrez la stratégie dans [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] .

   Une fois que vous avez enregistré la stratégie dans [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , vous ne pouvez plus modifier les paramètres des règles qui existent dans [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] uniquement.
