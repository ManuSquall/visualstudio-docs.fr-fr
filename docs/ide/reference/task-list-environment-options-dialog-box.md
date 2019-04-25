---
title: Liste des tâches, Environnement, boîte de dialogue Options
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
- VS.ToolsOptionsPages.Environment.TaskList
- VS.Environment.Task List
helpviewer_keywords:
- Token List
- tokens
- icons, in Task List
- Task List, customizing environment
- Options dialog box, Task List environment
- exclamation points
- comments, comment tasks in Task List
- tokens, and the Task List
- Task List, comment tasks
ms.assetid: 88327e04-fa3e-48db-995b-ad89e0dc4ed2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b2fc59a2f04dc30ef8b052e93fc6ffdf030e054
ms.sourcegitcommit: b14b7a938a2aba9fcce4d5e813aadf2040b0dcda
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58647217"
---
# <a name="options-dialog-box-environment--task-list"></a>Boîte de dialogue Options : Environnement \> Liste des tâches

Cette page Options vous permet d’ajouter, de supprimer et de modifier les jetons de commentaire qui génèrent des rappels de la **liste des tâches**. Pour afficher ces paramètres, sélectionnez **Options** dans le menu **Outils**, développez le dossier **Environnement**, puis choisissez **Liste des tâches**.

## <a name="task-list-tokens"></a>Jetons de la Liste des tâches

Quand vous insérez un commentaire dans votre code dont le texte commence par un jeton de la **liste des jetons**, la **Liste des tâches** affiche votre commentaire comme nouvelle entrée chaque fois que le fichier est ouvert pour modification. Cliquez sur une entrée de la **Liste des tâches** pour accéder directement à la ligne de commentaire dans votre code. Pour plus d’informations, consultez [Utilisation de la liste des tâches](../../ide/using-the-task-list.md).

Liste des jetons\
Affiche une liste de jetons, et vous permet d'ajouter ou de supprimer des jetons personnalisés. Les jetons de commentaire sont sensibles à la casse en C# et C++, mais pas en Visual Basic.

> [!NOTE]
> Si vous ne tapez pas le jeton souhaité exactement comme il apparaît dans la liste des jetons, aucune tâche de commentaire ne s’affiche dans **Liste des tâches**.

Priorité\
Définit la priorité des tâches qui utilisent le jeton sélectionné (basse, normale ou haute). Les commentaires de tâche qui commencent par ce jeton reçoivent automatiquement la priorité désignée dans **Liste des tâches**.

Nom\
Entrez la chaîne de jeton ici et cliquez sur **Ajouter** pour ajouter la chaîne à la liste des jetons.

Ajouter\
Activé quand vous entrez un nouveau **Nom**. Cliquez pour ajouter une nouvelle chaîne de jeton en utilisant les valeurs entrées dans les champs **Nom** et **Priorité**.

Supprimer\
Cliquez pour supprimer le jeton sélectionné de la liste des jetons. Vous ne pouvez pas supprimer le jeton de commentaire par défaut.

Changer\
Cliquez pour apporter des modifications à un jeton existant en utilisant les valeurs entrées dans les champs **Nom** et **Priorité**.

> [!NOTE]
> Vous ne pouvez pas renommer ou supprimer le jeton de commentaire par défaut, mais vous pouvez changer son niveau de priorité.

## <a name="see-also"></a>Voir aussi

- [Utilisation de la liste des tâches](../../ide/using-the-task-list.md)
- [Définition de signets dans le code](../../ide/setting-bookmarks-in-code.md)
- [Environnement, boîte de dialogue Options](../../ide/reference/environment-options-dialog-box.md)