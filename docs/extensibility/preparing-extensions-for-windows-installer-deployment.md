---
title: Préparation des Extensions pour le déploiement de Windows Installer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c958c75088a6e31d9386f1acd423360b8dbe0a6c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66336179"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Préparer des extensions pour le déploiement Windows Installer
Vous ne pouvez pas utiliser un package Windows Installer (MSI) pour déployer un package VSIX. Toutefois, vous pouvez extraire le contenu d’un package VSIX pour le déploiement du MSI. Ce document montre comment préparer un projet dont la sortie par défaut est un package VSIX pour l’inclusion dans un projet d’installation.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Préparer un projet d’extension pour le déploiement Windows Installer
 Effectuez ces étapes sur les nouveaux projets d’extension avant d’ajouter à un projet d’installation.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Pour préparer un projet d’extension pour le déploiement Windows Installer

1. Créer un VSPackage, composant MEF, éditeur ornement ou autre type de projet d’extensibilité qui inclut un manifeste VSIX.

2. Ouvrez le manifeste VSIX dans l’éditeur de code.

3. Définir le `InstalledByMsi` élément du manifeste VSIX pour `true`. Pour plus d’informations sur le manifeste VSIX, consultez [référence de schéma 2.0 d’extension VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).

     Cela empêche le programme d’installation VSIX installer le composant.

4. Cliquez sur le projet dans **l’Explorateur de solutions** et cliquez sur **propriétés**.

5. Sélectionnez le **VSIX** onglet.

6. Cochez la case intitulée **contenu VSIX de copie à l’emplacement suivant** et tapez le chemin d’accès où le projet d’installation collectera les fichiers.

## <a name="extract-files-from-an-existing-vsix-package"></a>Extrayez les fichiers à partir d’un package VSIX existant
 Suivez ces étapes pour ajouter le contenu d’un package VSIX existant à un projet d’installation lorsque vous n’avez pas les fichiers sources.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Pour extraire les fichiers à partir d’un package VSIX existant

1. Renommer le *. VSIX* fichier contenant l’extension à partir de *filename.vsix* à *filename.zip*.

2. Copiez le contenu de la *.zip* fichier dans un répertoire.

3. Supprimer le *[Content_types] .xml* fichier à partir du répertoire.

4. Modifier le manifeste VSIX, comme indiqué dans la procédure précédente.

5. Ajouter les fichiers restants à votre projet d’installation.

## <a name="see-also"></a>Voir aussi
- [Déploiement de programme d’installation de Visual Studio](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
- [Procédure pas à pas : Créer une action personnalisée](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))