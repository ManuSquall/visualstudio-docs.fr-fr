---
title: Préparation des extensions pour le déploiement de Windows Installer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 76d7f879fade99914bf3f56ade0ec1270e14f4c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694592"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Préparation d’extensions au déploiement de Windows Installer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous ne pouvez pas utiliser un package de Windows Installer (MSI) pour déployer un package VSIX. Toutefois, vous pouvez extraire le contenu d’un package VSIX pour le déploiement MSI. Ce document montre comment préparer un projet dont la sortie par défaut est un package VSIX à inclure dans un projet d’installation.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Préparation d’un projet d’extension pour le déploiement de Windows Installer  
 Effectuez ces étapes sur les nouveaux projets d’extension avant d’ajouter à un projet d’installation.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Pour préparer un projet d’extension pour le déploiement de Windows Installer  
  
1. Créez un VSPackage, un composant MEF, un ornement d’éditeur ou tout autre type de projet d’extensibilité qui comprend un manifeste VSIX.  
  
2. Ouvrez le manifeste VSIX dans l’éditeur de code.  
  
3. Affectez à l’élément InstalledByMsi du manifeste VSIX la valeur `true` . Pour plus d’informations sur le manifeste VSIX, consultez [Référence du schéma d’extension vsix 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Cela empêche le programme d’installation VSIX d’essayer d’installer le composant.  
  
4. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**.  
  
5. Sélectionnez l’onglet **VSIX** .  
  
6. Cochez la case **copier le contenu VSIX à l’emplacement suivant** et tapez le chemin d’accès à l’emplacement où le projet d’installation va récupérer les fichiers.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>Extraction de fichiers à partir d’un package VSIX existant  
 Procédez comme suit pour ajouter le contenu d’un package VSIX existant à un projet d’installation lorsque vous n’avez pas les fichiers sources.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Pour extraire des fichiers d’un package VSIX existant  
  
1. Renommez le. Fichier VSIX contenant l’extension de *nom*de fichier. VSIX dans *nom_fichier*. zip.  
  
2. Copiez le contenu du fichier. zip dans un répertoire.  
  
3. Supprimez le fichier [Content_types]. xml du répertoire.  
  
4. Modifiez le manifeste VSIX, comme indiqué dans la procédure précédente.  
  
5. Ajoutez les fichiers restants à votre projet d’installation.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement de Visual Studio Installer](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Procédure pas à pas : création d’une action personnalisée](https://msdn.microsoft.com/4bd4b63a-2b91-431e-839c-5752443f0eaf)
