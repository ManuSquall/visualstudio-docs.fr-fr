---
title: -Upgrade (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bb2b296d8728587c9aa3c22b7a670d89612eff1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596422"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)

Met le fichier solution et tous ses fichiers projet, ou le fichier projet spécifié, aux formats Visual Studio actuels pour ces fichiers.

## <a name="syntax"></a>Syntaxe

```shell
devenv {SolutionFile|ProjectFile} /Upgrade [/Out OutputFilename]
```

## <a name="arguments"></a>Arguments

- *SolutionFile*

  Requis en cas de mise à niveau d’une solution tout entière avec ses projets. Chemin et nom d’un fichier solution. Vous pouvez entrer uniquement le nom du fichier solution, ou un chemin complet et le nom du fichier solution. Si le dossier ou le fichier nommé n’existe pas encore, il est créé.

- *ProjectFile (projectFile)*

  Requis en cas de mise à niveau d’un seul projet. Chemin et nom d’un fichier projet dans la solution. Vous pouvez entrer uniquement le nom du fichier projet, ou un chemin complet et le nom du fichier projet. Si le dossier ou le fichier nommé n’existe pas encore, il est créé.

- `/Out`*OutputFilename (en)*

  facultatif. Nom du fichier auquel vous souhaitez envoyer la sortie de l’outil. Si le fichier existe déjà, l’outil ajoute la sortie à la fin du fichier.

## <a name="remarks"></a>Notes 

Les sauvegardes sont créées et copiées automatiquement dans un répertoire nommé Backup, créé dans le répertoire actif.

Les solutions ou projets sous contrôle de code source doivent être extraits avant de pouvoir être mis à niveau.

Le commutateur `/Upgrade` n’ouvre pas Visual Studio. Les résultats de la mise à niveau peuvent être vus dans le rapport de mise à niveau pour le langage de développement de la solution ou du projet. Aucune information d’erreur ni d’utilisation n’est retournée. Pour plus d’informations sur la mise à niveau de projets dans Visual Studio, voir [Porter, migrer et mettre à niveau des projets Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md).

## <a name="example"></a> Exemple

Cet exemple met à niveau un fichier solution nommé « MyProject.sln ».

```shell
devenv "%USERPROFILE%\source\repos\MyProject\MyProject.sln" /upgrade
```

## <a name="see-also"></a>Voir aussi

- [Commutateurs de ligne de commande Devenv](../../ide/reference/devenv-command-line-switches.md)
