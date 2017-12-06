---
title: Gestionnaire de package dans les Outils R pour Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 06/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 92644bcb21c23eb91ccd8223b99cce98ba4c57db
ms.sourcegitcommit: ae9450e81c4167b3fbc9ee5d1992fc693628eafa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2017
---
# <a name="package-manager"></a>Gestionnaire de package

Le Gestionnaire de package Outils R pour Visual Studio (RTVS) est une interface utilisateur pour la gestion des packages R. Pour l’ouvrir, sélectionnez **Outils R > Windows > Packages** ou appuyez sur Ctrl+7.

Le Gestionnaire de package comporte trois onglets. Chaque onglet affiche une liste des packages pertinents sur la gauche et des détails spécifiques sur le package sélectionné sur la droite, notamment la version, la description, la licence et l’emplacement d’installation du package, ainsi que des liens vers d’autres informations pertinentes. La zone de recherche dans le coin supérieur droit vous permet de filtrer la liste.

> [!Tip]
> Le terme dans la zone de recherche reste en vigueur quand vous basculez entre les onglets.

- **Disponible** vous permet de parcourir les packages à installer. Si le package est déjà installé, le bouton **Installer** à droite devient **Désinstaller**.

    ![Onglet Packages disponibles dans le Gestionnaire de package Outils R pour Visual Studio](media/package-manager-available.png)

- **Installé** affiche tous les packages installés et chargés. Un point vert en regard d’un package signifie qu’il est chargé dans la session R. Vous pouvez utiliser la croix rouge dans la liste de gauche ou le bouton **Désinstaller** à droite pour désinstaller le package. Si une version plus récente d’un package installé est disponible, une flèche bleue vers le haut affichée à droite du package permet d’effectuer la mise à jour.

    ![Onglet Packages installés dans le Gestionnaire de package Outils R pour Visual Studio](media/package-manager-installed.png)

- **Chargé** affiche uniquement les packages qui sont chargés dans la session R, lesquels comportent tous un point vert. Vous pouvez également désinstaller et mettre à jour des packages à partir de cet onglet.

    ![Onglet Packages chargés dans le Gestionnaire de package Outils R pour Visual Studio](media/package-manager-loaded.png)

## <a name="package-locations"></a>Emplacements des packages

Les packages sont installés aux emplacements suivants :

- Les packages de base fournis avec RTV sont installés dans `C:\Program Files\Microsoft\R Client\R_SERVER\library`.
- Les packages supplémentaires sont installés dans `%userprofile%\Documents\R\win-library\3.3`.
