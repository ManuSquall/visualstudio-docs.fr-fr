---
title: Compatibilité des versions des stratégies d’archivage de l’analyse du code
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41de42c02916165d9c0be91c6af5076279e0b4d4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922241"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Compatibilité des versions des stratégies d’archivage de l’analyse du code

Si vous devez évaluer et créer des stratégies analyse du code de vérification à l’aide de différentes versions de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], vous devez connaître les différences dans la manière dont [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] et [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] évaluer les stratégies d’archivage.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Compatibilité des versions d’évaluation des stratégies d’archivage

- Lorsque les stratégies d’archivage de l’analyse du code sont évalués dans [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], toutes les règles qui existaient dans [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] mais n’existent pas dans [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] sont ignorés.

- Lorsque les stratégies d’archivage de l’analyse du code sont évalués dans [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], toutes les nouvelles règles qui sont exclusives à [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] sont ignorés.

- Si la stratégie d’archivage de l’analyse du code spécifie des assemblys de règles, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignore toutes les règles qui sont spécifiées par les assemblys qu’il ne reconnaît pas.

- Si la stratégie d’archivage de l’analyse du code spécifie des assemblys de règles qui [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ne reconnaît pas, un message s’affiche.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Compatibilité des versions pour la création de stratégies d’archivage

- Si vous avez créé une stratégie d’archivage de l’analyse du code à l’aide de la [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] version de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], vous ne pouvez pas utiliser le [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] version de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] pour le modifier. Et également, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ne peut pas évaluer la stratégie.

- Si vous avez créé une stratégie d’archivage de l’analyse du code à l’aide de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] dans [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], vous pouvez utiliser [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] dans [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] pour modifier la stratégie et peut également être évalué que par [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. Après avoir modifié la stratégie à l’aide de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] dans [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], vous ne pouvez plus modifier la stratégie à l’aide de [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] dans [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] évaluer les stratégies sans problème avec des noms forts ne correspondent pas.

- Pour créer une stratégie d’archivage de l’analyse du code avec des paramètres de règle qui s’appliquent à la fois pour [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] et [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], vous devez créer la stratégie dans [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], apportez toutes les modifications nécessaires et enregistrer la stratégie. Si les modifications apportées aux règles existent uniquement dans [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], vous modifiez et enregistrez la stratégie dans [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].

   Après avoir enregistré la stratégie dans [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], vous ne pouvez plus modifier les paramètres des règles qui existent dans [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] uniquement.