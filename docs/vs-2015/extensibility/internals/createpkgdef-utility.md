---
title: Utilitaire CreatePkgDef | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ec77937e18ab437107b0e9d269fb4b5c7c8e2381
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503081"
---
# <a name="createpkgdef-utility"></a>Utilitaire CreatePkgDef
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [utilitaire CreatePkgDef](https://docs.microsoft.com/visualstudio/extensibility/internals/createpkgdef-utility).  
  
Prend un fichier .dll pour une extension Visual Studio en tant que paramètre et crée un fichier .pkgdef pour accompagner le fichier .dll. Le fichier .pkgdef contient toutes les informations qui seraient sinon écrits dans le Registre système lors de l’extension est installée.  
  
> [!NOTE]
>  La plupart des modèles de projet qui sont inclus dans le SDK Visual Studio automatiquement créer les fichiers .pkgdef en tant que partie du processus de génération. Ce document est destiné à ceux qui souhaitent créer manuellement des packages, ou convertir des packages existants pour utiliser un déploiement de .pkgdef.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Arguments  
 / out =`FileName`  
 Obligatoire. Définit le nom du fichier de sortie .pkgdef à`FileName`.  
  
 /codebase  
 Facultatif. Inscription de force avec l’utilitaire de base de code.  
  
 assembly  
 Inscription de force avec l’utilitaire de l’Assembly.  
  
 `AssemblyPath`  
 Le chemin d’accès du fichier .dll à partir de laquelle vous souhaitez générer le .pkgdef.  
  
## <a name="remarks"></a>Notes  
 Déploiement de l’extension à l’aide de fichiers .pkgdef remplace la configuration requise du Registre des versions antérieures de Visual Studio.  
  
 Les fichiers .pkgdef doivent être installés dans un des emplacements suivants : %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ ou %vsinstalldir%\Common7\IDE\Extensions\\. Si le dossier d’installation est %localappdata%\Microsoft\Visual Studio\14.0\Extensions\\, l’extension sera reconnue par Visual Studio, mais sera désactivée par défaut. L’utilisateur peut activer l’extension à l’aide de **Extensions et mises à jour**. Si le dossier d’installation est %vsinstalldir%\Common7\IDE\Extensions\\, l’extension est activée par défaut.  
  
> [!NOTE]
>  Le **Extensions et mises à jour** outil ne peut pas être utilisé pour accéder à une extension, sauf si elle est installée dans le cadre d’un package VSIX.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)

