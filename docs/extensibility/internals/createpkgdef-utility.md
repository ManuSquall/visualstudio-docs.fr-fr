---
title: Utilitaire de CreatePkgDef | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 32e9c8ffa2a9ca2bba889436f37cc4f5c3d188bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="createpkgdef-utility"></a>Utilitaire de CreatePkgDef
Accepte un fichier .dll pour une extension de Visual Studio en tant que paramètre et crée un fichier .pkgdef pour accompagner le fichier .dll. Le fichier .pkgdef contient toutes les informations qui sont sinon écrite dans le Registre système lors de l’extension est installée.  
  
> [!NOTE]
>  La plupart des modèles de projet qui sont inclus dans le Kit de développement logiciel Visual Studio automatiquement créer les fichiers de .pkgdef en tant que partie du processus de génération. Ce document est destiné à ceux qui souhaitent créer des packages manuellement, ou convertir des packages existants pour utiliser le déploiement .pkgdef.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Arguments  
 / out =`FileName`  
 Obligatoire. Définit le nom du fichier de sortie .pkgdef à`FileName`.  
  
 /codebase  
 Facultatif. Inscription de force avec l’utilitaire de base de code.  
  
 / assembly  
 Inscription de force avec l’utilitaire de l’Assembly.  
  
 `AssemblyPath`  
 Le chemin d’accès du fichier .dll à partir de laquelle vous souhaitez générer le .pkgdef.  
  
## <a name="remarks"></a>Remarques  
 Déploiement d’une extension à l’aide de fichiers de .pkgdef remplace la configuration requise du Registre des versions antérieures de Visual Studio.  
  
 Les fichiers .pkgdef doivent être installés dans un des emplacements suivants : %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ ou %vsinstalldir%\Common7\IDE\Extensions\\. Si le dossier d’installation est %localappdata%\Microsoft\Visual Studio\14.0\Extensions\\, l’extension est reconnue par Visual Studio, mais il sera désactivée par défaut. L’utilisateur peut activer l’extension à l’aide de **Extensions et mises à jour**. Si le dossier d’installation est %vsinstalldir%\Common7\IDE\Extensions\\, l’extension est activée par défaut.  
  
> [!NOTE]
>  Le **Extensions et mises à jour** outil ne peut pas être utilisé pour accéder à une extension, sauf si elle est installée en tant que partie d’un package VSIX.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)