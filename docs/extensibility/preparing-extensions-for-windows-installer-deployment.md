---
title: Préparation des extensions pour le déploiement de l’installateur Windows (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8636dfbbad06192e5edbb61a9a784f64b8f3f14f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702029"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Préparer les extensions pour le déploiement de Windows Installer
Vous ne pouvez pas utiliser un package d’installateur Windows (MSI) pour déployer un package VSIX. Toutefois, vous pouvez extraire le contenu d’un package VSIX pour le déploiement de MSI. Ce document montre comment préparer un projet dont la sortie par défaut est un package VSIX pour l’inclusion dans un projet d’installation.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Préparer un projet d’extension pour le déploiement de Windows Installer
 Effectuez ces étapes sur de nouveaux projets d’extension avant d’ajouter à un projet d’installation.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Préparer un projet d’extension pour le déploiement de Windows Installer

1. Créez un composant VSPackage, MEF, Editor Adornment ou tout autre type de projet d’extensibility qui comprend un manifeste VSIX.

2. Ouvrez le manifeste VSIX dans l’éditeur de code.

3. Définissez `InstalledByMsi` l’élément du `true`manifeste VSIX à . Pour plus d’informations sur le manifeste VSIX, voir [vsIX extension schéma 2.0 référence](../extensibility/vsix-extension-schema-2-0-reference.md).

     Cela empêche l’installateur VSIX de tenter d’installer le composant.

4. Cliquez à droite sur le projet dans **Solution Explorer** et cliquez sur **Propriétés**.

5. Sélectionnez l’onglet **VSIX.**

6. Cochez le contenu VSIX de copie étiqueté par boîte **à l’endroit suivant** et tapez le chemin vers l’endroit où le projet Setup reprendra les fichiers.

## <a name="extract-files-from-an-existing-vsix-package"></a>Extraire les fichiers d’un package VSIX existant
 Effectuez ces étapes pour ajouter le contenu d’un package VSIX existant à un projet d’installation lorsque vous n’avez pas les fichiers source.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Pour extraire des fichiers d’un package VSIX existant

1. Renommer le *. Fichier VSIX* contenant l’extension de *filename.vsix* à *filename.zip*.

2. Copiez le contenu du fichier *.zip* dans un répertoire.

3. Supprimer le fichier *[Content_types].xml* de l’annuaire.

4. Modifier le manifeste VSIX, comme indiqué dans la procédure précédente.

5. Ajoutez les fichiers restants à votre projet Setup.

## <a name="see-also"></a>Voir aussi
- [Déploiement d’installateur Visual Studio](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
- [Procédure pas à pas : Créez une action personnalisée](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))
