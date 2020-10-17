---
title: Guide pratique pour générer dans un répertoire de sortie commun
description: Découvrez comment vous pouvez modifier les chemins de sortie de la génération de vos projets pour forcer la mise en place de toutes les sorties dans le même dossier.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a39dae210c2cb9afe3e4b77962b75ddb3be4baeb
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136964"
---
# <a name="how-to-build-to-a-common-output-directory"></a>Guide pratique pour générer dans un répertoire de sortie commun

Par défaut, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] génère chaque projet dans une solution dans son propre dossier à l’intérieur de la solution. Vous pouvez changer les chemins de sortie de build de vos projets pour imposer que toutes les sorties soient placées dans le même dossier.

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Pour placer toutes les sorties de solution dans un répertoire commun

1. Cliquez sur un projet dans la solution.

2. Dans le menu **Projet** , cliquez sur **Propriétés**.

3. En fonction du type de projet, cliquez sur l’onglet **Compiler** ou sur l’onglet **Générer**, puis définissez comme **Chemin de sortie** un dossier à utiliser pour tous les projets de la solution.

4. Répétez les étapes 1 à 3 pour tous les projets de la solution.

## <a name="see-also"></a>Voir aussi

- [Compiler et générer](../ide/compiling-and-building-in-visual-studio.md)
- [Comment : modifier le répertoire de sortie de génération](../ide/how-to-change-the-build-output-directory.md)