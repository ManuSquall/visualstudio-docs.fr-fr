---
title: Liste des tâches, Environnement, boîte de dialogue Options | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31aa18a219d49f3f18e8b98fbe010141cf5e69c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="task-list-environment-options-dialog-box"></a>Liste des tâches, Environnement, boîte de dialogue Options
Cette page Options vous permet d’ajouter, de supprimer et de modifier les jetons de commentaire qui génèrent des rappels de la **liste des tâches**. Pour afficher ces paramètres, sélectionnez **Options** dans le menu **Outils**, développez le dossier **Environnement**, puis choisissez **Liste des tâches**.  
  
## <a name="task-list-options"></a>Options de la liste des tâches  
 Confirmer la suppression des tâches  
 Quand cette option est sélectionnée, une boîte de message s’affiche chaque fois qu’une tâche utilisateur est supprimée de la **liste des tâches**, ce qui vous permet de confirmer la suppression. Cette option est activée par défaut.  
  
> [!NOTE]
>  Pour supprimer un commentaire de tâche, cliquez sur le lien pour rechercher le commentaire, puis supprimez-le de votre code.  
  
 Afficher seulement les noms des fichiers  
 Quand cette option est sélectionnée, la colonne **Fichier** de la **liste des tâches** affiche seulement les noms des fichiers à modifier, mais pas leurs chemins complets.  
  
## <a name="tokens"></a>jetons  
 Quand vous insérez un commentaire dans votre code dont le texte commence par un jeton de la **liste des jetons**, la **liste des tâches** affiche votre commentaire comme nouvelle entrée chaque fois que le fichier est ouvert pour modification. Vous pouvez cliquer sur cette entrée de **liste des tâches** pour accéder directement à la ligne de commentaire dans votre code. Pour plus d’informations, consultez [Utilisation de la liste des tâches](../../ide/using-the-task-list.md).  
  
 Liste des jetons  
 Affiche une liste de jetons, et vous permet d'ajouter ou de supprimer des jetons personnalisés. Les jetons de commentaire respectent la casse dans C# et Visual C++, mais pas dans Visual Basic.  
  
> [!NOTE]
>  Si vous ne tapez pas le jeton souhaité exactement comme il apparaît dans la **liste des jetons**, aucune tâche de commentaire ne s’affichera dans la **liste des tâches**.  
  
 Priorité  
 Définit la priorité des tâches qui utilisent le jeton sélectionné. Les commentaires de tâche qui commencent par ce jeton reçoivent automatiquement la priorité désignée dans la **liste des tâches**.  
  
 Name  
 Entrez la chaîne du jeton. Cette opération active le bouton **Ajouter**. Si vous cliquez sur **Ajouter**, cette chaîne est incluse dans la **liste des jetons** et les commentaires qui commencent par ce nom sont affichés dans la **liste des tâches**.  
  
 Ajouter  
 Activé quand vous entrez un nouveau **Nom**. Cliquez pour ajouter une nouvelle chaîne de jeton en utilisant les valeurs entrées dans les champs **Nom** et **Priorité**.  
  
 Supprimer  
 Cliquez pour supprimer le jeton sélectionné de la **liste des jetons**. Vous ne pouvez pas supprimer le jeton de commentaire par défaut.  
  
 Modification  
 Cliquez pour apporter des modifications à un jeton existant en utilisant les valeurs entrées dans les champs **Nom** et **Priorité**.  
  
> [!NOTE]
>  Vous ne pouvez pas renommer ou supprimer le jeton de commentaire par défaut, mais vous pouvez changer son niveau de priorité.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de la liste des tâches](../../ide/using-the-task-list.md)   
 [Définition de signets dans le code](../../ide/setting-bookmarks-in-code.md)   
 [Environnement, boîte de dialogue Options](../../ide/reference/environment-options-dialog-box.md)