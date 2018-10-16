---
title: Préparation des Extensions pour le déploiement de Windows Installer | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4483fef9c200f6814c247f14ee956bfef4582e6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197923"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Préparation d’extensions au déploiement de Windows Installer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous ne pouvez pas utiliser un package Windows Installer (MSI) pour déployer un package VSIX. Toutefois, vous pouvez extraire le contenu d’un package VSIX pour le déploiement du MSI. Ce document montre comment préparer un projet dont la sortie par défaut est un package VSIX pour l’inclusion dans un projet d’installation.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Préparation d’un projet d’Extension pour le déploiement de Windows Installer  
 Effectuez ces étapes sur les nouveaux projets d’extension avant d’ajouter à un projet d’installation.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Pour préparer un projet d’extension pour le déploiement Windows Installer  
  
1.  Créer un VSPackage, composant MEF, éditeur ornement ou autre type de projet d’extensibilité qui inclut un manifeste VSIX.  
  
2.  Ouvrez le manifeste VSIX dans l’éditeur de code.  
  
3.  Définissez l’élément InstalledByMsi de manifeste VSIX pour `true`. Pour plus d’informations sur le manifeste VSIX, consultez [VSIX Extension de schéma 2.0 référence](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Cela empêche le programme d’installation VSIX installer le composant.  
  
4.  Cliquez sur le projet dans **l’Explorateur de solutions** et cliquez sur **propriétés**.  
  
5.  Sélectionnez le **VSIX** onglet.  
  
6.  Cochez la case intitulée **contenu VSIX de copie à l’emplacement suivant** et tapez le chemin d’accès où le projet d’installation collectera les fichiers.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>Extraction des fichiers à partir d’un Package VSIX existant  
 Suivez ces étapes pour ajouter le contenu d’un package VSIX existant à un projet d’installation lorsque vous n’avez pas les fichiers sources.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Pour extraire les fichiers à partir d’un package VSIX existant  
  
1.  Renommer le. Fichier VSIX contenant l’extension à partir de *filename*.vsix à *filename*.zip.  
  
2.  Copiez le contenu du fichier .zip dans un répertoire.  
  
3.  Supprimer le fichier [Content_types] .xml à partir du répertoire.  
  
4.  Modifier le manifeste VSIX, comme indiqué dans la procédure précédente.  
  
5.  Ajouter les fichiers restants à votre projet d’installation.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement de programme d’installation de Visual Studio](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Procédure pas à pas : Création d’une Action personnalisée](http://msdn.microsoft.com/en-us/4bd4b63a-2b91-431e-839c-5752443f0eaf)

