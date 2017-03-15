---
title: "Liste des t&#226;ches, Environnement, bo&#238;te de dialogue Options | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Environment.Task_List"
  - "VS.ToolsOptionsPag.Environment.Task_List"
  - "VS.ToolsOptionsPages.Environment.TaskList"
  - "VS.Environment.Task List"
helpviewer_keywords: 
  - "Liste des jetons"
  - "jetons"
  - "icônes, dans la Liste des tâches"
  - "Liste des tâches, personnalisation de l’environnement"
  - "Options (boîte de dialogue), environnement Liste des tâches"
  - "points d'exclamation"
  - "commentaires, tâches de commentaire dans la Liste des tâches"
  - "jetons et Liste des tâches"
  - "Liste des tâches, tâches de commentaires"
ms.assetid: 88327e04-fa3e-48db-995b-ad89e0dc4ed2
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Liste des t&#226;ches, Environnement, bo&#238;te de dialogue Options
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette page Options vous permet d'ajouter, supprimer et modifier les jetons de commentaire qui génèrent des rappels de la **Liste des tâches**.  Pour afficher ces paramètres, sélectionnez **Options** dans le menu **Outils**, développez le dossier **Environnement**, puis choisissez**Liste des tâches**.  
  
## Options de la liste des tâches  
 Confirmer la suppression des tâches  
 Quand cette option est sélectionnée, un message s'affiche chaque fois qu'une tâche utilisateur est supprimée de la **Liste des tâches**, ce qui vous permet de confirmer la suppression.  Cette option est activée par défaut.  
  
> [!NOTE]
>  Pour supprimer un commentaire de tâche, cliquez sur le lien pour rechercher le commentaire, puis supprimez\-le de votre code.  
  
 Afficher seulement les noms des fichiers  
 Quand cette option est sélectionnée, la colonne **Fichier** de la **Liste des tâches** affiche seulement les noms des fichiers à modifier, mais pas leurs chemins d'accès complets.  
  
## Jetons  
 Quand vous insérez un commentaire dans votre code dont le texte commence par un jeton de la **Liste des jetons**, la **Liste des tâches** affiche votre commentaire comme nouvelle entrée quand le fichier est ouvert pour modification.  Vous pouvez cliquer sur cette **Liste des tâches** pour accéder directement à la ligne de commentaire dans votre code.  Pour plus d'informations, consultez [Utilisation de la liste des tâches](../../ide/using-the-task-list.md).  
  
 Liste des jetons  
 Affiche une liste de jetons, et vous permet d'ajouter ou de supprimer des jetons personnalisés.  Les jetons de commentaire respectent la casse dans Visual C\# et Visual C\+\+, mais pas dans Visual Basic.  
  
> [!NOTE]
>  Si vous ne tapez pas le jeton souhaité exactement comme il apparaît dans la **Liste des jetons**, une tâche de commentaire ne s'affichera pas dans la **Liste des tâches**.  
  
 Priorité  
 Définit la priorité des tâches qui utilisent le jeton sélectionné.  Les commentaires de tâche qui commencent par ce jeton sont automatiquement affectés de la priorité désignée dans la **Liste des tâches**.  
  
 Nom  
 Entrez la chaîne du jeton.  Cette opération active le bouton **Ajouter**.  Si vous cliquez sur **Ajouter**, cette chaîne est incluse dans la **Liste des jetons** et les commentaires qui commencent par ce nom sont affichés dans la **Liste des tâches**.  
  
 Ajouter  
 Activé quand vous entrez un nouveau **Nom**.  Cliquez pour ajouter une nouvelle chaîne de jeton en utilisant les valeurs entrées dans les champs **Nom** et **Priorité**.  
  
 Supprimer  
 Cliquez pour supprimer le jeton sélectionné de la **Liste des jetons**.  Vous ne pouvez pas supprimer le jeton de commentaire par défaut.  
  
 Modifier  
 Cliquez pour apporter des modifications à un jeton existant en utilisant les valeurs entrées dans les champs **Nom** et **Priorité**.  
  
> [!NOTE]
>  Vous ne pouvez pas renommer ou supprimer le jeton de commentaire par défaut, mais vous pouvez changer son niveau de priorité.  
  
## Voir aussi  
 [Utilisation de la liste des tâches](../../ide/using-the-task-list.md)   
 [Définition de signets dans le code](../../ide/setting-bookmarks-in-code.md)   
 [Environnement, boîte de dialogue Options](../../ide/reference/environment-options-dialog-box.md)