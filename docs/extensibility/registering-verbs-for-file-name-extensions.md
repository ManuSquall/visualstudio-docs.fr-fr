---
title: Enregistrement des verbes pour les extensions de nom de fichier (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac2854f1799075cc14d9beb557335be5228be21d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701532"
---
# <a name="register-verbs-for-file-name-extensions"></a>Enregistrer les verbes pour les extensions de nom de fichier
L’association d’une extension de nom de fichier avec une application a généralement une action préférée qui se produit quand un utilisateur double-clics d’un fichier. Cette action préférée est liée à un verbe, par exemple ouvert, qui correspond à l’action.

 Vous pouvez enregistrer les verbes associés à un identifiant programmatique (ProgID) pour une extension en utilisant la clé Shell située à **HKEY_CLASSES_ROOT\{progidô shell**. Pour plus d’informations, voir [les types de fichiers](/windows/desktop/shell/fa-file-types).

## <a name="register-standard-verbs"></a>Enregistrer les verbes standard
 Le système d’exploitation reconnaît les verbes standard suivants :

- Ouvrir

- Modifier

- Lire

- Print

- PRÉVERSION

  Dans la mesure du possible, enregistrez un verbe standard. Le choix le plus commun est le verbe ouvert. Utilisez le verbe Edit uniquement s’il y a une nette différence entre l’ouverture du fichier et l’édition du fichier. Par exemple, l’ouverture d’un fichier *.htm* l’affiche dans le navigateur, tandis que l’édition d’un fichier *.htm* démarre un éditeur HTML. Les verbes standard sont localisés avec le local du système d’exploitation.

> [!NOTE]
> Lors de l’enregistrement des verbes standard, ne définissez pas la valeur par défaut pour la clé Open. La valeur par défaut contient la chaîne d’affichage sur le menu. Le système d’exploitation fournit cette chaîne pour les verbes standard.

 Les fichiers de projet doivent être [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] enregistrés pour démarrer une nouvelle instance de l’ouverture du fichier par un utilisateur. L’exemple suivant illustre l’inscription [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] standard d’un verbe pour un projet.

```
[HKEY_CLASSES_ROOT\.csproj]
@="VisualStudio.csproj.8.0"

[HKEY_CLASSES_ROOT\.csproj\OpenWithList]
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]
@=""

[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]
"VisualStudio.csproj.8.0"=""

[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]
@="C# Project file"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""
```

 Pour ouvrir un fichier dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]un cas existant de , enregistrez une clé DDEEXEC. L’exemple suivant illustre l’enregistrement [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] standard d’un verbe standard pour un fichier *.cs.*

```
[HKEY_CLASSES_ROOT\.cs]
@="VisualStudio.cs.8.0"

[HKEY_CLASSES_ROOT\.cs\OpenWithList]
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]
@=""

[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]
"VisualStudio.cs.8.0"=""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]
@="C# Source file"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]
@="Open(\"%1\")"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]
@="VisualStudio.8.0"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]
@="system"
```

## <a name="set-the-default-verb"></a>Définir le verbe par défaut
 Le verbe par défaut est l’action qui est exécutée lorsqu’un utilisateur double-clics d’un fichier dans Windows Explorer. Le verbe par défaut est le verbe spécifié comme la valeur par défaut pour la **\\HKEY_CLASSES_ROOT*clé progid*Shell.** Si aucune valeur n’est spécifiée, le verbe par défaut est le premier verbe spécifié dans la liste de clés **\\*HKEY_CLASSES_ROOT progid*Shell.**

> [!NOTE]
> Si vous prévoyez de modifier le verbe par défaut pour une extension dans un déploiement côte à côte, tenez compte de l’impact sur l’installation et l’enlèvement. Lors de l’installation, la valeur par défaut d’origine est écrasée.

## <a name="see-also"></a>Voir aussi
- [Gérer les associations de fichiers côte à côte](../extensibility/managing-side-by-side-file-associations.md)
