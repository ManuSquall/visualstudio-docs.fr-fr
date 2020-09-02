---
title: Liste des tâches, Environnement, boîte de dialogue Options | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
- VS.ToolsOptionsPag.Environment.Task_List
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
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72e5f82fa3ca4b7ca909ee07e5b77a31b3e20879
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72650974"
---
# <a name="task-list-environment-options-dialog-box"></a>Liste des tâches, Environnement, boîte de dialogue Options
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette page Options vous permet d’ajouter, de supprimer et de modifier les jetons de commentaire qui génèrent des rappels de la **liste des tâches**. Pour afficher ces paramètres, sélectionnez **Options** dans le menu **Outils**, développez le dossier **Environnement**, puis choisissez **Liste des tâches**.

## <a name="task-list-options"></a>Options de la liste des tâches
 Confirmer la suppression des tâches lorsque cette option est sélectionnée, une boîte de message s’affiche chaque fois qu’une tâche utilisateur est supprimée de la **liste des tâches**, ce qui vous permet de confirmer la suppression. Cette option est activée par défaut.

> [!NOTE]
> Pour supprimer un commentaire de tâche, cliquez sur le lien pour rechercher le commentaire, puis supprimez-le de votre code.

 Afficher les noms de fichiers uniquement lorsque cette option est sélectionnée, la colonne **fichier** de la **liste des tâches** affiche uniquement les noms des fichiers à modifier, et non leurs chemins d’accès complets.

## <a name="tokens"></a>Jetons
 Quand vous insérez un commentaire dans votre code dont le texte commence par un jeton de la **liste des jetons**, la **liste des tâches** affiche votre commentaire comme nouvelle entrée chaque fois que le fichier est ouvert pour modification. Vous pouvez cliquer sur cette entrée de **liste des tâches** pour accéder directement à la ligne de commentaire dans votre code. Pour plus d’informations, consultez [Utilisation de la liste des tâches](../../ide/using-the-task-list.md).

 Liste des jetons affiche une liste de jetons, et vous permet d’ajouter ou de supprimer des jetons personnalisés. Les jetons de commentaire respectent la casse dans Visual C# et Visual C++, mais pas dans Visual Basic.

> [!NOTE]
> Si vous ne tapez pas le jeton souhaité exactement comme il apparaît dans la **liste des jetons**, aucune tâche de commentaire ne s’affichera dans la **liste des tâches**.

 Priorité définit la priorité des tâches qui utilisent le jeton sélectionné. Les commentaires de tâche qui commencent par ce jeton reçoivent automatiquement la priorité désignée dans la **liste des tâches**.

 Nom entrez la chaîne de jeton. Cette opération active le bouton **Ajouter**. Si vous cliquez sur **Ajouter**, cette chaîne est incluse dans la **liste des jetons** et les commentaires qui commencent par ce nom sont affichés dans la **liste des tâches**.

 Ajouter activé lorsque vous entrez un nouveau **nom**. Cliquez pour ajouter une nouvelle chaîne de jeton en utilisant les valeurs entrées dans les champs **Nom** et **Priorité**.

 Supprimer cliquez sur cette option pour supprimer le jeton sélectionné de la **liste des jetons**. Vous ne pouvez pas supprimer le jeton de commentaire par défaut.

 Modifier cliquez pour apporter des modifications à un jeton existant en utilisant les valeurs entrées dans les champs **nom** et **priorité** .

> [!NOTE]
> Vous ne pouvez pas renommer ou supprimer le jeton de commentaire par défaut, mais vous pouvez changer son niveau de priorité.

## <a name="see-also"></a>Voir aussi
 [Utilisation de la liste des tâches](../../ide/using-the-task-list.md) [définir des signets dans la boîte de](../../ide/setting-bookmarks-in-code.md) [dialogue Options d’environnement](../../ide/reference/environment-options-dialog-box.md) de code
