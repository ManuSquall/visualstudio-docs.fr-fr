---
title: Préparation des extensions pour le déploiement de Windows Installer | Microsoft Docs
description: Découvrez comment préparer un projet dont la sortie par défaut est un package VSIX à inclure dans un projet d’installation.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6436d05d3b15be1c1fe8d7c7bb9c8592dee091dc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090276"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Préparer les extensions pour le déploiement de Windows Installer
Vous ne pouvez pas utiliser un package de Windows Installer (MSI) pour déployer un package VSIX. Toutefois, vous pouvez extraire le contenu d’un package VSIX pour le déploiement MSI. Ce document montre comment préparer un projet dont la sortie par défaut est un package VSIX à inclure dans un projet d’installation.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Préparer un projet d’extension pour le déploiement de Windows Installer
 Effectuez ces étapes sur les nouveaux projets d’extension avant d’ajouter à un projet d’installation.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Pour préparer un projet d’extension pour le déploiement de Windows Installer

1. Créez un VSPackage, un composant MEF, un ornement d’éditeur ou tout autre type de projet d’extensibilité qui comprend un manifeste VSIX.

2. Ouvrez le manifeste VSIX dans l’éditeur de code.

3. Affectez `InstalledByMsi` à l’élément du manifeste VSIX la valeur `true` . Pour plus d’informations sur le manifeste VSIX, consultez [Référence du schéma d’extension vsix 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).

     Cela empêche le programme d’installation VSIX d’essayer d’installer le composant.

4. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**.

5. Sélectionnez l’onglet **VSIX** .

6. Cochez la case **copier le contenu VSIX à l’emplacement suivant** et tapez le chemin d’accès à l’emplacement où le projet d’installation va récupérer les fichiers.

## <a name="extract-files-from-an-existing-vsix-package"></a>Extraire les fichiers d’un package VSIX existant
 Procédez comme suit pour ajouter le contenu d’un package VSIX existant à un projet d’installation lorsque vous n’avez pas les fichiers sources.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Pour extraire des fichiers d’un package VSIX existant

1. Renommez le *. Fichier VSIX* contenant l’extension de *nom de fichier. vsix* à *filename.zip*.

2. Copiez le contenu du fichier *. zip* dans un répertoire.

3. Supprimez le fichier *[Content_Types]. xml* du répertoire.

4. Modifiez le manifeste VSIX, comme indiqué dans la procédure précédente.

5. Ajoutez les fichiers restants à votre projet d’installation.

## <a name="see-also"></a>Voir aussi
- [Déploiement du programme d’installation de Visual Studio](/previous-versions/2kt85ked(v=vs.120))
- [Procédure pas à pas : créer une action personnalisée](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))