---
title: "G&#233;n&#233;ral, Environnement, bo&#238;te de dialogue Options | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Message.0x800a002e"
  - "VS.ToolsOptionsPages.Environment.General"
  - "VS.Environment.General"
helpviewer_keywords: 
  - "listes utilisées récemment"
  - "fenêtres, personnalisation"
  - "MDI, options d’environnement"
  - "vitesse, animation d’environnement"
  - "menu Fichier"
  - "menus, personnalisation"
  - "personnalisation des menus Windows"
  - "barres d’état, affichage"
  - "page de démarrage de Visual Studio, définition"
  - "IDE, options de démarrage"
  - "éditeurs, saisie semi-automatique"
  - "Options (boîte de dialogue),environnement général"
  - "Environnement général, boîte de dialogue Options"
ms.assetid: 90fc2e6f-572f-4384-96d8-5678299ce58e
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 34
---
# G&#233;n&#233;ral, Environnement, bo&#238;te de dialogue Options
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilisez cette page pour modifier les thèmes de couleurs, les paramètres de la barre d'état et les associations d'extensions de fichier, entre autres options, pour l'environnement de développement intégré \(IDE\).  Pour accéder à la boîte de dialogue **Options**, ouvrez le menu **Outils**, choisissez **Options**, ouvrez le dossier **Environnement**, puis choisissez la page **Général**.  Si cette page n'apparaît pas dans la liste, cochez la case **Afficher tous les paramètres** dans la boîte de dialogue **Options**.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour changer vos paramètres, ouvrez le menu **Outils**, puis choisissez **Importation et exportation de paramètres**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Expérience visuelle  
 **Thème de couleurs**  
 Choisissez le thème de couleurs **Bleu**, **Clair** ou **Foncé** pour l'IDE.  
  
 Vous pouvez installer d'autres thèmes prédéfinis et créer des thèmes personnalisés en téléchargeant et en installant l'**éditeur de thème de couleur de Visual Studio 2015** à partir de la [galerie Visual Studio](https://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=RootCategory&f%5B0%5D.Value=tools).  Une fois cet outil installé, d'autres thèmes de couleurs apparaissent dans la zone de liste des thèmes de couleurs.  
  
 Appliquer une 1ère lettre en majuscules à la barre de menus  
 Les initiales des menus sont en **majuscules** par défaut dans Visual Studio 2015.  Désélectionnez cette option pour les définir sur **Tout en majuscules**.  
  
 **Ajuster automatiquement l'expérience visuelle selon les perf. du client**  
 Spécifie si Visual Studio définit automatiquement le réglage de l'expérience visuelle ou si vous vous en chargez explicitement.  Ce réglage peut changer l'affichage des couleurs, depuis des dégradés jusqu'à des couleurs simples, ou limiter l'utilisation des animations dans les menus ou les fenêtres contextuelles.  
  
 **Activer l'expérience client améliorée**  
 Active l'expérience visuelle complète de Visual Studio, y compris les dégradés et les animations.  Désactivez cette option lors de l'utilisation de connexions Bureau à distance ou de cartes graphiques anciennes, car les performances de ces fonctionnalités peuvent se révéler médiocres dans ces cas.  Cette option est disponible seulement quand vous désactivez l'option **Ajuster automatiquement l'expérience visuelle selon les perf. du client**.  
  
 **Utiliser l'accélération graphique matérielle si elle est disponible**  
 Utilise l'accélération graphique matérielle si elle est disponible, au lieu de l'accélération logicielle.  
  
## Autre  
 **Éléments affichés dans le menu Fenêtre**  
 Personnalise le nombre de fenêtres qui s'affichent dans la liste Fenêtres du menu **Fenêtre**.  Entrez un nombre compris entre 1 et 24.  Par défaut, ce nombre est de 10.  
  
 **Éléments affichés dans la liste des fichiers récents**  
 Personnalise le nombre de projets et de fichiers les plus récemment utilisés qui s'affichent sur le menu **Fichier**.  Entrez un nombre compris entre 1 et 24.  Par défaut, ce nombre est de 10.  Il s'agit d'un moyen facile de récupérer les projets et les fichiers récemment utilisés.  
  
 **Afficher la barre d'état**  
 Affiche la barre d'état.  La barre d'état se trouve en bas de la fenêtre de l'IDE et affiche des informations sur la progression des opérations en cours.  
  
 **Le bouton Fermer n'affecte que la fenêtre Outil active**  
 Spécifie que quand l'utilisateur clique sur le bouton **Fermer**, seule la fenêtre Outil qui a le focus est fermée et non pas toutes les fenêtres Outil de l'ensemble ancré.  Cette option est activée par défaut.  
  
 **Le bouton Masquer automatiquement n'affecte que la fenêtre Outil active**  
 Spécifie que quand l'utilisateur clique sur le bouton **Masquer automatiquement**, seule la fenêtre Outil qui a le focus est masquée automatiquement et non pas toutes les fenêtres Outil de l'ensemble ancré.  Cette option est désactivée par défaut.  
  
 **Gérer les associations de fichiers**  
 Affiche la boîte de dialogue **Windows définit les associations de programmes**, où vous pouvez afficher les extensions de fichiers des éléments qui sont généralement associés à Visual Studio, et le programme par défaut en cours pour ouvrir chaque type de fichier.  Pour faire de Visual Studio l'application par défaut pour les types de fichiers qui n'y sont pas déjà associés, choisissez l'extension de fichier, puis choisissez **Enregistrer**.  
  
 Cette option peut être utile si vous avez deux versions de Visual Studio installées sur le même ordinateur et que vous désinstallez l'une des versions plus tard.  Après la désinstallation, les icônes des fichiers Visual Studio n'apparaissent plus dans l'Explorateur de fichiers.  En outre, Windows ne reconnaît plus Visual Studio comme application par défaut pour modifier ces fichiers.  Cette option restaure ces associations.  
  
## Voir aussi  
 [Environnement, boîte de dialogue Options](../../ide/reference/environment-options-dialog-box.md)   
 [Personnalisation des dispositions de fenêtres](../../ide/customizing-window-layouts-in-visual-studio.md)