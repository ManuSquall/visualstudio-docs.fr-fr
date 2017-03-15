---
title: "Lancement rapide, Environnement, bo&#238;te de dialogue Options | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Environment.QuickLaunch"
  - "vs.quicklaunch"
helpviewer_keywords: 
  - "rechercher l'IDE"
  - "IDE, recherche"
ms.assetid: 4200f297-d065-4723-9a30-d91ff2e26c9d
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Lancement rapide, Environnement, bo&#238;te de dialogue Options
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Vous pouvez utiliser **Lancement rapide** pour rechercher et exécuter rapidement des actions pour les ressources de l'IDE, comme les options, les modèles ou les menus.  Vous ne pouvez pas utiliser **Lancement rapide** pour rechercher du code et des symboles.  La zone de recherche **Lancement rapide** se trouve dans le coin supérieur droit de la barre de menus et est accessible via Ctrl\+Q.  Entrez simplement votre chaîne de recherche dans la zone.  Pour rechercher des chaînes qui contiennent des @, utilisez @@.  
  
 Le **Lancement rapide** est activé par défaut quand vous installez Visual Studio.  Dans la barre de menus, vous pouvez afficher ou masquer **Lancement rapide** en choisissant **Outils**, **Options**.  Développez le nœud **Environnements**, puis choisissez **Lancement rapide**.  Cochez ou décochez la case **Activer le menu de lancement rapide**.  Vous pouvez également activer ou désactiver des catégories de recherche sur cette page.  
  
## Liste des catégories  
 Les résultats de recherche du Lancement rapide apparaissent dans quatre catégories :**Les dernières utilisées**, **Menus**, **Options** et **Documents ouverts**, ainsi que le nombre d'éléments de la catégorie.  Pour parcourir les résultats de la recherche par catégorie, choisissez Ctrl\+Q pour afficher tous les résultats de la catégorie suivante.  Une fois la dernière catégorie affichée, Ctrl\+Q vous montre quelques résultats de chaque catégorie.  Vous pouvez utiliser Ctrl\+Maj\+Q pour naviguer dans les catégories dans l'ordre inverse.  Pour afficher tous les résultats de recherche d'une catégorie, choisissez le nom de la catégorie.  
  
 Vous pouvez utiliser les raccourcis suivants pour limiter votre recherche à des catégories spécifiques.  
  
|Catégorie|Raccourci|Description du raccourci|  
|---------------|---------------|------------------------------|  
|Les dernières utilisées|@mru<br /><br /> Par exemple, `@mru police`|Affiche jusqu'à cinq éléments qui sont les **Derniers utilisés**.|  
|Menus|@menu<br /><br /> Par exemple, `@menu police`|Limite la recherche aux éléments de menu.|  
|Options|@opt<br /><br /> Par exemple, `@opt police`|Limite la recherche aux paramètres de la boîte de dialogue **Options**.|  
|Documents|@doc<br /><br /> Par exemple, `@doc police`|Limite la recherche aux noms et aux chemins d'accès de fichiers des documents ouverts pour les critères de recherche, mais ne recherche pas le texte dans les fichiers eux\-mêmes.|  
  
> [!NOTE]
>  Vous pouvez changer les touches de raccourci dans la page **Général**, **Clavier** de la boîte de dialogue **Options**.  
  
## Afficher les résultats précédents  
 Par défaut, le terme de recherche que vous entrez n'est pas conservé entre les sessions de recherche.  La chaîne de recherche est effacée si vous recherchez un terme, que vous déplacez le curseur en dehors de la zone **Lancement rapide**, puis que vous y revenez.  Pour conserver les résultats de recherche, accédez à la boîte de dialogue **Options**, choisissez **Lancement rapide**, puis cochez la case **Afficher les résultats de la dernière recherche si le menu de lancement rapide est activé**.  La prochaine fois que vous effectuez une recherche, quittez la zone Lancement rapide et revenez\-y : la zone Lancement rapide conserve alors le dernier terme de recherche utilisé et vous montre également les résultats de recherche.  
  
 Pour les conseils et astuces les plus récents pour l'utilisation de la zone **Lancement rapide**, consultez [le blog Visual Studio](http://go.microsoft.com/fwlink/?LinkId=236054).  
  
## Voir aussi  
 [Éléments généraux de l'interface utilisateur \(Visual Studio\)](../../ide/reference/general-user-interface-elements-visual-studio.md)   
 [Environnement, boîte de dialogue Options](../../ide/reference/environment-options-dialog-box.md)