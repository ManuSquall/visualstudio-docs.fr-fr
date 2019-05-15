---
title: Utilitaire CreatePkgDef | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84f5e7db4b31607c05da32a09e5d691a85ef4173
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65614825"
---
# <a name="createpkgdef-utility"></a>Utilitaire CreatePkgDef
Prend un fichier .dll pour une extension Visual Studio en tant que paramètre et crée un *.pkgdef* fichier pour accompagner le *.dll* fichier. Le *.pkgdef* fichier contient toutes les informations qui seraient sinon écrits dans le Registre système lors de l’extension est installée.

> [!NOTE]
> La plupart des modèles de projet qui sont inclus automatiquement dans le SDK Visual Studio créent *.pkgdef* fichiers dans le cadre du processus de génération. Ce document est destiné à ceux qui souhaitent créer manuellement des packages, ou convertir des packages existants à utiliser *.pkgdef* déploiement.

## <a name="syntax"></a>Syntaxe

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Arguments
**/out=&lt;FileName&gt;**\
Obligatoire. Définit le nom de la *.pkgdef* fichier de sortie &lt;FileName&gt;.

**/codebase**\
Facultatif. Force l’inscription avec le **CodeBase** utilitaire.

**/assembly**\
Force l’inscription avec le **Assembly** utilitaire.

**&lt;AssemblyPath&gt;**\
Le chemin d’accès de la *.dll* fichier à partir de laquelle vous souhaitez générer le *.pkgdef*.

## <a name="remarks"></a>Notes
Déploiement à l’aide de l’extension *.pkgdef* fichiers remplace la configuration requise du Registre des versions antérieures de Visual Studio.

::: moniker range=">=vs-2019"

Le *.pkgdef* fichiers doivent être installés dans un des emplacements suivants :

- *%LocalAppData%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Si le dossier d’installation est *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*, l’extension n’est reconnue par Visual Studio, mais est désactivée par défaut. L’utilisateur peut activer l’extension à l’aide de **gérer les Extensions**.

Si le dossier d’installation est *%vsinstalldir%\Common7\IDE\Extensions\\*, l’extension est activée par défaut.

> [!NOTE]
> Le **gérer les Extensions** outil ne peut pas être utilisé pour accéder à une extension, sauf si elle est installée dans le cadre d’un package VSIX.

::: moniker-end

::: moniker range="vs-2017"

Le *.pkgdef* fichiers doivent être installés dans un des emplacements suivants :

- *%LocalAppData%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Si le dossier d’installation est *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*, l’extension n’est reconnue par Visual Studio, mais est désactivée par défaut. L’utilisateur peut activer l’extension à l’aide de **Extensions et mises à jour**.

Si le dossier d’installation est *%vsinstalldir%\Common7\IDE\Extensions\\*, l’extension est activée par défaut.

> [!NOTE]
> Le **Extensions et mises à jour** outil ne peut pas être utilisé pour accéder à une extension, sauf si elle est installée dans le cadre d’un package VSIX.

::: moniker-end

## <a name="see-also"></a>Voir aussi
- [Utilitaire CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)
