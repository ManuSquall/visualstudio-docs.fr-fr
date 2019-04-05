---
title: Utilitaire CreatePkgDef | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f450453ce8e336fecb401e30bc777c7b9c8ef7d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950029"
---
# <a name="createpkgdef-utility"></a>Utilitaire CreatePkgDef
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Prend un fichier .dll pour une extension Visual Studio en tant que paramètre et crée un fichier .pkgdef pour accompagner le fichier .dll. Le fichier .pkgdef contient toutes les informations qui seraient sinon écrits dans le Registre système lors de l’extension est installée.  
  
> [!NOTE]
>  La plupart des modèles de projet qui sont inclus dans le SDK Visual Studio automatiquement créer les fichiers .pkgdef en tant que partie du processus de génération. Ce document est destiné à ceux qui souhaitent créer manuellement des packages, ou convertir des packages existants pour utiliser un déploiement de .pkgdef.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Arguments  
 /out=`FileName`  
 Obligatoire. Définit le nom du fichier de sortie .pkgdef à`FileName`.  
  
 /codebase  
 Optionnel. Inscription de force avec l’utilitaire de base de code.  
  
 /assembly  
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
