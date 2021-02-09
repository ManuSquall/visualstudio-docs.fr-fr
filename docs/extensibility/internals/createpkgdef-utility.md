---
title: Utilitaire CreatePkgDef | Microsoft Docs
description: En savoir plus sur l’utilitaire CreatePkgDef qui accepte un fichier. dll pour une extension Visual Studio en tant que paramètre et crée un fichier. pkgdef pour accompagner le fichier. dll.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f9822319a74d1374ef2a88d4f9231e6fd86b1e5f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884531"
---
# <a name="createpkgdef-utility"></a>Utilitaire CreatePkgDef
Accepte un fichier. dll pour une extension Visual Studio en tant que paramètre et crée un fichier *. pkgdef* pour accompagner le fichier *. dll* . Le fichier *. pkgdef* contient toutes les informations qui seraient autrement écrites dans le registre système lorsque l’extension est installée.

> [!NOTE]
> La plupart des modèles de projet inclus dans le kit de développement logiciel (SDK) Visual Studio créent automatiquement des fichiers *. pkgdef* dans le cadre du processus de génération. Ce document est destiné aux personnes qui veulent créer des packages manuellement ou convertir des packages existants pour utiliser le déploiement *. pkgdef*  .

## <a name="syntax"></a>Syntaxe

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Arguments
**/out = &lt; nom de fichier&gt;**\
Obligatoire. Définit le nom du fichier de sortie *. pkgdef* sur &lt; filename &gt; .

**/codebase**\
Facultatif. Force l’inscription avec l’utilitaire **code base** .

**/assembly**\
Force l’inscription avec l’utilitaire d' **assembly** .

**&lt;AssemblyPath&gt;**\
Chemin d’accès du fichier *. dll* à partir duquel vous souhaitez générer le *. pkgdef*.

## <a name="remarks"></a>Notes
Le déploiement d’extension à l’aide de fichiers *. pkgdef* remplace les spécifications de registre des versions antérieures de Visual Studio.

::: moniker range=">=vs-2019"

Les fichiers *. pkgdef* doivent être installés dans l’un des emplacements suivants :

- *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Si le dossier d’installation est *%LocalAppData%\Microsoft\Visual \\ Studio\16.0\Extensions*, l’extension est reconnue par Visual Studio, mais elle est désactivée par défaut. L’utilisateur peut activer l’extension à l’aide de la **gestion des extensions**.

Si le dossier d’installation *est \\ %VSInstallDir%\Common7\IDE\Extensions*, l’extension est activée par défaut.

> [!NOTE]
> L’outil **gérer les extensions** ne peut pas être utilisé pour accéder à une extension, sauf si elle est installée dans le cadre d’un package VSIX.

::: moniker-end

::: moniker range="vs-2017"

Les fichiers *. pkgdef* doivent être installés dans l’un des emplacements suivants :

- *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Si le dossier d’installation est *%LocalAppData%\Microsoft\Visual \\ Studio\15.0\Extensions*, l’extension est reconnue par Visual Studio, mais elle est désactivée par défaut. L’utilisateur peut activer l’extension à l’aide d' **extensions et de mises à jour**.

Si le dossier d’installation *est \\ %VSInstallDir%\Common7\IDE\Extensions*, l’extension est activée par défaut.

> [!NOTE]
> L’outil **extensions et mises à jour** ne peut pas être utilisé pour accéder à une extension, sauf s’il est installé dans le cadre d’un package VSIX.

::: moniker-end

## <a name="see-also"></a>Voir aussi
- [Utilitaire CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
