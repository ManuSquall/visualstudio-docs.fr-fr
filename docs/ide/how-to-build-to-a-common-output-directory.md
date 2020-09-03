---
title: Guide pratique pour générer dans un répertoire de sortie commun
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
ms.openlocfilehash: 9a499b5ca5ea64dd9ded10f82b1af43258f346d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85284774"
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