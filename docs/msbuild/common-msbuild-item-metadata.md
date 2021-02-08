---
title: Métadonnées d’élément MSBuild communes | Microsoft Docs
description: Découvrez les métadonnées d’élément facultatives qui ont une signification pour certains SDK ou cibles MSBuild, mais qui ne sont pas définies par défaut pour chaque élément.
ms.custom: SEO-VS-2020
ms.date: 07/13/2020
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- msbuild, common item metadata
- item metadata (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8dda627f748773bc4cb5598b133ac05597ffe1d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839307"
---
# <a name="common-msbuild-item-metadata"></a>Métadonnées communes d’éléments MSBuild

Le tableau suivant décrit les métadonnées d’élément facultatives qui ont une signification pour certains kits de développement logiciel (SDK) MSBuild ou cibles, mais qui ne sont pas définis par défaut pour chaque élément. Vous pouvez les définir pour influencer le comportement de la génération, mais uniquement si le kit de développement logiciel (SDK) ou les fichiers cibles que vous utilisez le reconnaissent.

| Métadonnées d’élément | Kits SDK | Description |
|---------------| ------- | -------------|
|% (Lien)| Tous |Le système de projet Visual Studio utilise des `Link` métadonnées (le cas échéant) pour modifier les éléments qui s’affichent dans l’arborescence de projet ; vous pouvez placer un fichier dans une structure de dossiers logiques différente dans **Explorateur de solutions**.<br />En outre, la `AssignTargetPath` tâche examine `Link` pour déterminer où copier un fichier dans le répertoire de sortie, s’il s’agit de l’un des éléments copiés.|
|% (Lien ressources)| SDK .NET Core | Utilisé pour définir le dossier à utiliser pour les `Link` métadonnées des groupes d’éléments. |

## <a name="see-also"></a>Voir aussi

- [Propriétés communes des projets MSBuild](../msbuild/common-msbuild-project-properties.md)
- [Éléments communs des projets MSBuild](../msbuild/common-msbuild-project-items.md)
- [Métadonnées d’éléments connus MSBuild](msbuild-well-known-item-metadata.md)