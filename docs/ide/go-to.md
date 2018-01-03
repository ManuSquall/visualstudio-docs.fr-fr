---
title: "Rechercher du code à l’aide des commandes Atteindre | Microsoft Docs"
ms.custom: 
ms.date: 09/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509b2107-23d1-4fb3-987f-ab99ef45b72e
helpviewer_keywords:
- code editor, go to
- code editor, go to line
- go to line
- go to
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9309a143760aab5b59355b4cea6cd214aaa49812
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="find-code-using-go-to-commands"></a>Rechercher du code à l’aide des commandes Atteindre  
Les commandes **Atteindre** de Visual Studio vous permettent d’effectuer une recherche ciblée dans votre code pour trouver rapidement des éléments spécifiques. Vous pouvez atteindre une ligne, un type, un symbole, un fichier ou un membre spécifique à partir d’une interface unifiée simple. Cette fonctionnalité existe dans Visual Studio 2017 et ultérieur.  

### <a name="how-to-use-it"></a>Utilisation  

Entrée        | Fonction 
------------ | ---
**Clavier** | Appuyez sur **Ctrl+T** ou **Ctrl+,**     
**Souris**    | Sélectionnez **Edition**, **Atteindre**, **Atteindre tout**  

Par défaut, une petite fenêtre s’affiche en haut à droite de votre éditeur de code.  

![Atteindre tout](media/gotoall.png)

À mesure que vous tapez dans la zone de texte, les résultats s’affichent dans une liste déroulante sous la zone de texte. Pour accéder à un élément, sélectionnez-le dans la liste.    

![Fenêtre Naviguer vers](../ide/media/vside_navigatetowindow.png "Fenêtre Naviguer vers")  

Vous pouvez aussi entrer un point d’interrogation (?) pour obtenir une aide supplémentaire.  

  ![Aide sur Atteindre tout](media/gotoall_help.png)

### <a name="filtered-searches"></a>Recherches filtrées  
Par défaut, l’élément spécifié est recherché dans tous les éléments de solution. Toutefois, vous pouvez limiter votre recherche de code à des types d’éléments spécifiques en faisant précéder les termes de recherche de certains caractères. Vous pouvez aussi changer rapidement le filtre de recherche en choisissant des boutons dans la barre d’outils de la boîte de dialogue Atteindre. Les boutons qui changent les filtres de type se trouvent à gauche, et les boutons qui changent l’étendue de recherche se trouvent à droite.  

![Atteindre des membres](../ide/media/vside_navigation_toolbar.png)

#### <a name="filter-to-a-specific-type-of-code-element"></a>Filtrer sur un type spécifique d’élément de code  
Pour limiter votre recherche à un type spécifique d’élément de code, vous pouvez spécifier un préfixe dans la zone de recherche ou sélectionner l’une des cinq icônes de filtre ci-dessous :  

Préfixe | Icône | Raccourci | Description
:----: | ---- | -------- | ---
\#      | ![Icône de symbole](media/gotoall_symbolicon.png) | Ctrl+1, Ctrl+S | Atteindre le symbole spécifié
f      | ![Icône de fichier](media/gotoall_fileicon.png)     | Ctrl+1, Ctrl+F | Atteindre le fichier spécifié
m      | ![Icône Membre](media/gotoall_membericon.png) | Ctrl+1, Ctrl+M | Atteindre le membre spécifié
t      | ![Icône de type](media/gotoall_typeicon.png)     | Ctrl+1, Ctrl+T | Atteindre le type spécifié
:      | ![Icône de ligne](media/gotoall_lineicon.png)     | CTRL+G         | Atteindre le numéro de ligne spécifié

#### <a name="filter-to-a-specific-location"></a>Filtrer sur un emplacement spécifique    
Pour limiter votre recherche à un emplacement spécifique, sélectionnez l’une des deux icônes de document ci-dessous :  

Icône | Description
---- | ---
![Document actif](media/gotoall_currentdocument.png) | Rechercher dans le document actif uniquement
![Documents externes](media/gotoall_external.png) | Rechercher dans des documents externes en plus de ceux qui se trouvent dans le projet ou la solution  

### <a name="camel-casing"></a>Casse mixte  
Si vous utilisez une [casse mixte](https://en.wikipedia.org/wiki/Camel_case) dans votre code, vous pouvez trouver plus rapidement des éléments de code en entrant uniquement les lettres majuscules de leur nom. Par exemple, si votre code dispose d’un type appelé `CredentialViewModel`, vous pouvez affiner la recherche en choisissant le filtre Type ("t"), puis en entrant simplement les lettres majuscules du nom (`CVM`) dans la boîte de dialogue Atteindre. Cette fonctionnalité peut être particulièrement utile si votre code contient des noms longs.  

![Fenêtre Naviguer vers - recherche en lettres majuscules](../ide/media/vside_capitalsearch.png)

### <a name="settings"></a>Paramètres  
Sélectionnez l’icône d’engrenage ![Icône d’engrenage](media/gotoall_gear.png) si vous souhaitez changer le comportement de cette fonctionnalité :  

Paramètre | Description
------- | ---
Utiliser l'onglet d'aperçu | Afficher l’élément sélectionné immédiatement dans l’onglet d’aperçu de l’IDE
Afficher les détails    | Afficher les informations sur un projet, un fichier et une ligne, et un récapitulatif des commentaires de documentation dans la fenêtre
Centrer la fenêtre   | Déplacer cette fenêtre pour qu’elle s’affiche en haut au centre de l’éditeur de code, au lieu d’en haut à droite   

## <a name="see-also"></a>Voir aussi  
[Navigation dans le code](../ide/navigating-code.md)  
[Atteindre la définition et Aperçu de la définition](../ide/go-to-and-peek-definition.md)  