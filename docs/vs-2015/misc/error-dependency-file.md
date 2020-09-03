---
title: 'Erreur : impossible de copier le fichier de dépendance &#39;&#39; dans le projet &#39;Project&#39; dans le répertoire d’exécution, car il est en conflit avec le &#39;de fichiers de dépendance | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.tasklisterror.copy_version_conflict
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5d4fd45741585aaf82c82257999b40d6257e82d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656044"
---
# <a name="error-the-dependency-39file39-in-project-39project39-cannot-be-copied-to-the-run-directory-because-it-would-conflict-with-dependency-39file39"></a>Erreur : impossible de copier le fichier de &#39;de dépendance&#39; dans le projet &#39;Project&#39; dans le répertoire d’exécution, car il est en conflit avec le fichier de &#39;de dépendance&#39;
Il existe un conflit entre des références, car plusieurs dépendances distinctes qui portent le même nom de fichier sont copiées dans le répertoire bin pour permettre à l’application de s’exécuter. Le répertoire d’exécution ne peut pas résoudre le conflit dans la mesure où aucune des dépendances n’est une référence principale.

 Cette erreur entraîne l’échec de la build.

 Le fait de double-cliquer sur cet élément de la liste des tâches vous conduit au nœud de références du projet où le conflit se présente.

 **Pour corriger cette erreur**

- Configurez l’un des assemblys en référence directe de votre projet. Cette approche présente toutefois un inconvénient potentiel, puisqu’il n’est pas garanti que l’assembly que vous choisissez fonctionne avec les assemblys qui nécessitent une autre version de l’assembly référencé.

     \- ou -

- Vérifiez que les deux copies de l’assembly portent un nom fort et se trouvent dans le Global Assembly Cache. Ceci élimine le besoin de copier les assemblys dans le répertoire bin.

## <a name="see-also"></a>Voir aussi
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md) [global assembly cache](https://msdn.microsoft.com/library/cf5eacd0-d3ec-4879-b6da-5fd5e4372202) [assemblys assembly avec nom fort](https://msdn.microsoft.com/library/d4a80263-f3e0-4d81-9b61-f0cbeae3797b) contrôle de [version](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) [Comment : créer et supprimer des dépendances de projet](../ide/how-to-create-and-remove-project-dependencies.md)