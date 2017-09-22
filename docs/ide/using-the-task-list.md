---
title: "Utilisation de la liste des tâches | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
ms.assetid: f46a75a8-47b3-4cb6-bb59-b72e3356a664
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 01e8f3cc1bbcc2bc4b2fc94df1dad7d248b67290
ms.contentlocale: fr-fr
ms.lasthandoff: 02/22/2017

---
# <a name="using-the-task-list"></a>Utilisation de la liste des tâches
Avec la **liste des tâches** , effectuez le suivi des commentaires de code qui utilisent des jetons tels que `TODO` et `HACK`, ou des jetons personnalisés, et gérez les raccourcis qui permettent d’accéder directement à un emplacement prédéfini dans le code. Cliquez sur l’élément dans la liste pour accéder à son emplacement dans le code source.  
  
 Dans cette rubrique :  
  
-   [Fenêtre Liste des tâches](../ide/using-the-task-list.md#taskListWindow)  
  
-   [Tâches utilisateur](../ide/using-the-task-list.md#userTasks)  
  
-   [Jetons et commentaires](../ide/using-the-task-list.md#tokensComments)  
  
-   [Jetons personnalisés](../ide/using-the-task-list.md#customTokens)  
  
-   [Commentaires TODO C++](../ide/using-the-task-list.md#cppComments)  
  
-   [Raccourcis](../ide/using-the-task-list.md#shortcuts)  
  
##  <a name="taskListWindow"></a> Fenêtre Liste des tâches  
 Quand la **Liste des tâches** est ouverte, elle apparaît en bas de la fenêtre d’application.  
  
#### <a name="to-open-the-task-list"></a>Pour ouvrir la fenêtre Liste des tâches  
  
-   Dans le menu **Affichage**, choisissez **Liste des tâches** (clavier : Ctrl+\\,T).  
  
     ![Fenêtre Liste des tâches](../ide/media/vs2015_task_list.png "vs2015_task_list")  
  
#### <a name="to-change-the-sort-order-of-the-list"></a>Pour modifier l'ordre de tri de la liste  
  
-   Cliquez sur l'en-tête d'une colonne quelconque. Pour affiner vos résultats de recherche, appuyez sur Maj et cliquez sur un deuxième en-tête de colonne.  
  
     Comme alternative, dans le menu contextuel, vous pouvez choisir **Trier par**, puis choisir un en-tête. Pour affiner vos résultats de recherche, appuyez sur Maj et choisissez un deuxième en-tête de colonne.  
  
#### <a name="to-show-or-hide-columns"></a>Pour afficher ou masquer des colonnes  
  
-   Dans le menu contextuel, choisissez **Afficher les colonnes**. Choisissez les colonnes que vous souhaitez afficher ou masquer.  
  
#### <a name="to-change-the-order-of-the-columns"></a>Pour modifier l'ordre des colonnes  
  
-   Faites glisser n'importe quel en-tête de colonne à l'emplacement de votre choix.  
  
##  <a name="userTasks"></a> Tâches utilisateur  
 La fonctionnalité des tâches utilisateur a été supprimée dans Visual Studio 2015. Quand vous ouvrez une solution qui comporte des données de tâches utilisateur de Visual Studio 2013 et versions antérieures dans Visual Studio 2015, les données de tâches utilisateur dans votre fichier .suo ne sont pas affectées, mais les tâches utilisateur ne sont pas affichées dans la liste des tâches.  
  
 Si vous voulez continuer à accéder aux données de tâches utilisateur et les mettre à jour, vous devez ouvrir le projet dans Visual Studio 2013 et copier le contenu de toutes les tâches utilisateur dans votre outil de gestion de projet par défaut (tel que Team Foundation Server).  
  
##  <a name="tokensComments"></a> Jetons et commentaires  
 Un commentaire dans votre code, précédé d'un marqueur de commentaire et d'un jeton prédéfini, apparaîtra également dans la fenêtre **Liste des tâches** . Par exemple, le commentaire C# suivant comprend trois parties distinctes :  
  
-   le marqueur de commentaire (`//`) ;  
  
-   le jeton, par exemple (`TODO`) ;  
  
-   le commentaire (le reste du texte).  
  
```  
// TODO: Load state from previously suspended application  
```  
  
 Étant donné que `TODO` est un jeton prédéfini, ce commentaire s’affiche comme une tâche `TODO` dans la liste.  
  
###  <a name="customTokens"></a> Jetons personnalisés  
 Par défaut, Visual Studio inclut les jetons suivants : HACK, TODO, UNDONE, NOTE. Ces jetons ne respectent pas la casse.  
  
 Vous pouvez également créer vos propres jetons personnalisés.  
  
##### <a name="to-create-a-custom-token"></a>Pour créer un jeton personnalisé  
  
1.  Dans le menu **Outils** , choisissez **Options**.  
  
2.  Ouvrez le dossier **Environnement** , puis choisissez **Liste des tâches**.  
  
     La boîte de dialogue [Liste des tâches, Environnement, Options](../ide/reference/task-list-environment-options-dialog-box.md) s’affiche.  
  
     ![Liste des tâches Visual Studio](../ide/media/vs2015_task_list_options.png "vs2015_task_list_options")  
  
3.  Dans la catégorie **Jetons** , dans la zone de texte **Nom** , entrez le nom du jeton, par exemple « BOGUE ».  
  
4.  Dans la liste déroulante **Priorité** , choisissez une priorité par défaut pour le nouveau jeton. Choisissez le bouton **Ajouter** .  
  
###  <a name="cppComments"></a> Commentaires TODO C++  
 Par défaut, les commentaires TODO C++ sont affichés dans la fenêtre **Liste des tâches** . Vous pouvez modifier ce comportement.  
  
##### <a name="to-turn-off-c-todo-comments"></a>Pour désactiver les commentaires TODO C++  
  
1.  Dans le menu **Outils**, accédez à **Options &#124; Éditeur de texte &#124; C/C++ &#124; Affichage &#124; Énumérer les tâches de commentaire**, puis définissez la valeur sur false.  
  
2.  Dans la boîte de dialogue **Options** , ouvrez l' **Éditeur de texte**.  
  
3.  Sous **C/C++**, choisissez **Affichage**, puis affectez à **Énumérer les tâches de commentaire** la valeur **False**.  
  
##  <a name="shortcuts"></a> Raccourcis  
 Un *raccourci* est un signet dans le code qui est suivi dans la **Liste des tâches** ; son icône est différente de celle d’un signet normal. Double-cliquez sur le raccourci dans la fenêtre **Liste des tâches** pour accéder à l'emplacement correspondant dans le code.  
  
 ![Icône de raccourci de la liste des tâches Visual Studio](../ide/media/vs2015_task_list_bookmark.png "vs2015_task_list_bookmark")  
  
#### <a name="to-create-a-shortcut"></a>Pour créer un raccourci  
  
-   Insérez le pointeur dans le code à l'emplacement où vous souhaitez placer un raccourci. Choisissez **Edition &#124; Signets &#124; Ajouter un raccourci vers la liste des tâches** ou appuyez sur (clavier : Ctrl+K, Ctrl+H).  
  
     Pour parcourir les raccourcis figurant dans le code, choisissez un raccourci dans la liste, puis **Tâche suivante** ou **Tâche précédente** dans le menu contextuel.  
  
## <a name="see-also"></a>Voir aussi  
 [Liste des tâches, Environnement, boîte de dialogue Options](../ide/reference/task-list-environment-options-dialog-box.md)
