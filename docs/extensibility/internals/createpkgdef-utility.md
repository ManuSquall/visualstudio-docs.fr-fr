---
title: CreatePkgDef Utilitaire (fr) Microsoft Docs
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f437eb3586dc16bb0b4b9eb60cd303eb90db6c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709168"
---
# <a name="createpkgdef-utility"></a>Utilitaire CreatePkgDef
Prend un fichier .dll pour une extension Visual Studio comme paramètre et crée un fichier *.pkgdef* pour accompagner le fichier *.dll.* Le fichier *.pkgdef* contient toutes les informations qui seraient autrement écrites au registre du système lorsque l’extension est installée.

> [!NOTE]
> La plupart des modèles de projet qui sont inclus dans le Visual Studio SDK créent automatiquement des fichiers *.pkgdef* dans le cadre du processus de construction. Ce document est destiné à ceux qui veulent créer des paquets manuellement, ou convertir les paquets existants pour utiliser le déploiement *.pkgdef.*

## <a name="syntax"></a>Syntaxe

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Arguments
**(out)&lt;Nom de fichier&gt;**\
Obligatoire. Définit le nom du fichier de sortie &lt; *.pkgdef* à FileName&gt;.

**/base de code**\
facultatif. L’enregistrement des forces auprès de l’utilitaire **CodeBase.**

**/assemblage**\
L’enregistrement des forces auprès de **l’entreprise de l’Assemblée.**

**&lt;AssemblyPath (en)&gt;**\
Le chemin du fichier *.dll* à partir duquel vous voulez générer le *.pkgdef*.

## <a name="remarks"></a>Notes
Le déploiement d’extension en utilisant des fichiers *.pkgdef* remplace les exigences de registre des versions antérieures de Visual Studio.

::: moniker range=">=vs-2019"

Les fichiers *.pkgdef* doivent être installés dans l’un des endroits suivants :

- *%localappdata%-Microsoft-Visual Studio 16.0 -Extensions\\*

- *%vsinstalldir%-Common7-IDE-Extensions\\*

Si le dossier d’installation est *%localappdata%-Microsoft-Visual Studio-16.0 -Extensions\\*, l’extension est reconnue par Visual Studio mais est désactivée par défaut. L’utilisateur peut activer l’extension en utilisant **Manage Extensions**.

Si le dossier d’installation est *%vsinstalldir%-Common7-IDE-Extensions\\*, l’extension est activée par défaut.

> [!NOTE]
> **L’outil Manage Extensions** ne peut pas être utilisé pour accéder à une extension à moins qu’il ne soit installé dans le cadre d’un package VSIX.

::: moniker-end

::: moniker range="vs-2017"

Les fichiers *.pkgdef* doivent être installés dans l’un des endroits suivants :

- *%localappdata%-Microsoft-Visual Studio 15.0 -Extensions\\*

- *%vsinstalldir%-Common7-IDE-Extensions\\*

Si le dossier d’installation est *%localappdata%-Microsoft-Visual Studio-15.0 'Extensions\\*, l’extension est reconnue par Visual Studio, mais est désactivée par défaut. L’utilisateur peut activer l’extension en utilisant **des extensions et des mises à jour**.

Si le dossier d’installation est *%vsinstalldir%-Common7-IDE-Extensions\\*, l’extension est activée par défaut.

> [!NOTE]
> **L’outil Extensions et Mises à jour** ne peut pas être utilisé pour accéder à une extension à moins qu’il ne soit installé dans le cadre d’un package VSIX.

::: moniker-end

## <a name="see-also"></a>Voir aussi
- [CréerExpInstance utilitaire](../../extensibility/internals/createexpinstance-utility.md)
