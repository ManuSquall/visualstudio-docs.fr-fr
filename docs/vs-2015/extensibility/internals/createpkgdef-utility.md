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
ms.openlocfilehash: 010ee75efd84f016b0eb68fa9f715102026a4678
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839341"
---
# <a name="createpkgdef-utility"></a>Utilitaire CreatePkgDef
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Accepte un fichier. dll pour une extension Visual Studio en tant que paramètre et crée un fichier. pkgdef pour accompagner le fichier. dll. Le fichier. pkgdef contient toutes les informations qui seraient autrement écrites dans le registre système lorsque l’extension est installée.  
  
> [!NOTE]
> La plupart des modèles de projet inclus dans le kit de développement logiciel (SDK) Visual Studio créent automatiquement des fichiers. pkgdef dans le cadre du processus de génération. Ce document est destiné aux personnes qui veulent créer des packages manuellement ou convertir des packages existants pour utiliser le déploiement. pkgdef.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Arguments  
 /out =`FileName`  
 Obligatoire. Définit le nom du fichier de sortie. pkgdef sur `FileName` .  
  
 /codebase  
 facultatif. Force l’inscription avec l’utilitaire code base.  
  
 /assembly  
 Force l’inscription avec l’utilitaire d’assembly.  
  
 `AssemblyPath`  
 Chemin d’accès du fichier. dll à partir duquel vous souhaitez générer le. pkgdef.  
  
## <a name="remarks"></a>Remarques  
 Le déploiement d’extension à l’aide de fichiers. pkgdef remplace les spécifications de registre des versions antérieures de Visual Studio.  
  
 Les fichiers. pkgdef doivent être installés dans l’un des emplacements suivants :%localappdata%\Microsoft\Visual Studio\14.0\Extensions\ ou%vsinstalldir%\Common7\IDE\Extensions \\ . Si le dossier d’installation est%localappdata%\Microsoft\Visual Studio\14.0\Extensions \\ , l’extension sera reconnue par Visual Studio, mais elle sera désactivée par défaut. L’utilisateur peut activer l’extension à l’aide d' **extensions et de mises à jour**. Si le dossier d’installation est%vsinstalldir%\Common7\IDE\Extensions \\ , l’extension est activée par défaut.  
  
> [!NOTE]
> L’outil **extensions et mises à jour** ne peut pas être utilisé pour accéder à une extension, sauf s’il est installé dans le cadre d’un package VSIX.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
