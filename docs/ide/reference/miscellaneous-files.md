---
title: Fichiers divers
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], miscellaneous
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 793500faf217c74772506b4b7394d926447ffd40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75585295"
---
# <a name="miscellaneous-files"></a>Fichiers divers

Vous pouvez utiliser l’éditeur Visual Studio pour travailler sur des fichiers indépendamment d’un projet ou d’une solution. Dans une solution ouverte, vous pouvez ouvrir et modifier des fichiers sans les ajouter à une solution ou un projet. Les fichiers avec lesquels vous voulez travailler indépendamment sont appelés des « fichiers divers ». Les fichiers divers sont externes aux solutions et projets, et ne sont pas inclus dans les générations. Ils ne peuvent pas être inclus dans une solution sous contrôle de code source.

L’ouverture de fichiers indépendamment d’un projet ou d’une solution est pratique pour différentes raisons. Par exemple, vous voulez visualiser un fichier pendant le développement d’une solution basée sur un projet, mais qui ne fait pas partie du développement de la solution. Il s’agit souvent de remarques ou d’instructions concernant le développement, de schéma de base de données et d’extraits de code. Autre exemple, vous voulez créer un fichier autonome.

![Projets de solutions](../../ide/reference/media/projects_solutions_misc.gif)

Explorateur de solutions pouvez afficher un dossier **fichiers divers** pour les fichiers si les options du dossier sont activées. Les options peuvent être définies dans [Documents, Environnement, boîte de dialogue Options](../../ide/reference/documents-environment-options-dialog-box.md). Une fois que vous fermez un fichier divers, il n’est associé à aucune solution ou projet particulier, sauf si une option est activée dans ce but.

Le dossier **fichiers divers** représente les fichiers en tant que liens. Bien que ce dossier ne fasse pas partie d’une solution, quand vous ouvrez une solution, tout ou partie des fichiers divers qui étaient ouverts lors de la dernière fermeture de la solution sont rouverts, selon les paramètres définis pour le dossier.

> [!NOTE]
> Certains des fichiers qui n’apparaissent pas dans le dossier **fichiers divers** sont des fichiers que vous ne pouvez pas modifier dans l’IDE, tels que des fichiers. zip et des fichiers. doc. L’IDE n’effectue pas le suivi des fichiers qui ne peuvent être modifiés que par un éditeur externe.

## <a name="commands-available-in-the-ide"></a>Commandes disponibles dans l’IDE

Les menus, les barres d’outils et les commandes qu’ils contiennent changent selon le format du fichier que vous ouvrez. Quand vous ouvrez un fichier texte, par exemple, la barre d’outils Éditeur de texte apparaît et ses commandes sont disponibles. Si vous ouvrez un fichier de schéma XML, la barre d’outils du schéma XML s’affiche. Quand vous modifiez votre schéma XML, les commandes de la barre d’outils Éditeur de texte (ou la barre d’outils elle-même) ne sont pas disponibles. Le schéma XML est la fenêtre active. De ce fait, il hérite du contexte de sélection actuel. Quand vous passez d’un fichier projet à un fichier divers, toutes les commandes associées au projet disparaissent et seules celles directement associées au fichier divers s’affichent.

## <a name="folder-display-options"></a>Options d’affichage du dossier

Vous pouvez définir les options d’affichage du dossier **Fichiers divers** pour qu’il apparaisse même si vous n’avez ouvert aucun fichier divers. Le fichier solution ne gère pas la liste des fichiers divers de façon permanente. Il utilise une fonctionnalité facultative qui lui permet de garder en mémoire la liste des fichiers récemment utilisés par utilisateur.

## <a name="see-also"></a>Voir aussi

- [Développer du code dans Visual Studio sans projets ni solutions](../develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Solutions et projets](../../ide/solutions-and-projects-in-visual-studio.md)
- [Documents, environnement, boîte de dialogue Options](../../ide/reference/documents-environment-options-dialog-box.md)
