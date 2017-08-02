---
title: Atteindre | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 509b2107-23d1-4fb3-987f-ab99ef45b72e
author: BrianPeek
ms.author: brpeek
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3b812629bf0f655f39c35a56eb1b3ca9113303a6
ms.openlocfilehash: 8bf6d49b21d128d15f5312fb230d4a8e7a8195af
ms.lasthandoff: 03/01/2017

---

# <a name="go-to"></a>Atteindre
Il existe plusieurs façons de parcourir facilement votre code à l’intérieur de l’IDE de Visual Studio, à partir du clavier et de la souris.

<!-- VERSIONLESS -->
## <a name="go-to-all"></a>Atteindre tout
Cette fonctionnalité existe dans Visual Studio 2017 et ultérieur.  Elle vous permet de parcourir votre code pour trouver les éléments spécifiques que vous recherchez.  Vous pouvez rechercher entre autres une ligne, un type, un symbole ou un fichier spécifique à partir d’une interface unifiée simple.

### <a name="how-to-use"></a>Utilisation
* **Clavier**
  * Appuyez sur **Ctrl+,** ou **Ctrl+T**.  (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
* **Souris**
  * Sélectionnez **Edition > Atteindre > Atteindre tout**.

Par défaut, une petite fenêtre s’affiche en haut à droite de votre IDE.

![Atteindre tout](~/ide/media/gotoall.png)

À ce stade, il existe plusieurs façons de procéder :
* Entrez du texte sans préfixe pour rechercher à l’aide des [icônes de filtre](#filtered-searches) sélectionnés sous la zone de texte.
* Entrez un [préfixe](#filtered-searches) suivi du texte à rechercher.
* Entrez un point d’interrogation (?) pour obtenir une aide supplémentaire.
  ![Aide sur Accéder à tout](~/ide/media/gotoall_help.png)

### <a name="filtered-searches"></a>Recherches filtrées
Pour affiner votre recherche à un type spécifique, vous pouvez utiliser un préfixe lors de la saisie, ou utiliser les icônes sous la fenêtre de recherche, comme indiqué ci-dessous.

Préfixe | Icône | Raccourci | Description
:----: | ---- | -------- | ---
#      | ![Icône de symbole](~/ide/media/gotoall_symbolicon.png) | Ctrl+1, Ctrl+S | Rechercher des symboles correspondants
f      | ![Icône de fichier](~/ide/media/gotoall_fileicon.png)     | Ctrl+1, Ctrl+F | Rechercher des noms de fichiers correspondants
m      | ![Icône Membre](~/ide/media/gotoall_membericon.png) | Ctrl+1, Ctrl+M | Rechercher des membres correspondants
t      | ![Icône de type](~/ide/media/gotoall_typeicon.png)     | Ctrl+1, Ctrl+T | Rechercher des types correspondants
:      | ![Icône de ligne](~/ide/media/gotoall_lineicon.png)     | Ctrl+G         | Atteindre le numéro de ligne entré

### <a name="search-locations"></a>Emplacements de recherche
Pour affiner votre recherche à des emplacements spécifiques, utilisez les deux icônes de documents.

Icône | Description
---- | ---
![Document actif](~/ide/media/gotoall_currentdocument.png) | Rechercher dans le document actif uniquement
![Documents externes](~/ide/media/gotoall_external.png) | Rechercher dans des documents externes en plus de ceux qui se trouvent dans le projet ou la solution

### <a name="settings"></a>Paramètres
Un clic sur l’icône d’engrenage ![Icône d’engrenage](~/ide/media/gotoall_gear.png) dans l’angle inférieur droit vous permet de modifier le fonctionnement de cette fonctionnalité.

Paramètre | Description
------- | ---
Utiliser l'onglet d'aperçu | Afficher l’élément sélectionné immédiatement dans l’onglet d’aperçu de l’IDE
Afficher les détails    | Afficher des informations sur le projet, les fichiers et les lignes, ainsi qu’un résumé des commentaires de documentation dans la fenêtre
Centrer la fenêtre   | Déplacer cette fenêtre vers le centre de l’IDE au lieu de l’angle supérieur droit
<!-- END VERSIONLESS -->

## <a name="go-to-definition"></a>Atteindre la définition
Accéder à la source d’un type et ouvrir le résultat dans un nouvel onglet :

Entrée        | Fonction 
------------ | ---
**Clavier** | Placez le curseur de texte à l’intérieur du nom de type, puis appuyez sur **F12**.
**Souris**    | Cliquez avec le bouton droit sur le nom de type et sélectionnez **Atteindre la définition**.

## <a name="peek-definition"></a>Aperçu de la définition
Afficher un aperçu de la définition d’un type dans une fenêtre contextuelle au lieu d’un nouvel onglet :

Entrée        | Fonction 
------------ | ---
**Clavier** | Placez le curseur de texte à l’intérieur du nom de type, puis appuyez sur **Alt+F12**.
**Souris**    | Cliquez avec le bouton droit sur le nom de type et sélectionnez **Aperçu de la définition**.

Si vous affichez un aperçu d’une autre définition à partir de la fenêtre contextuelle, vous commencerez un chemin de fil d’Ariane que vous pourrez parcourir à l’aide des cercles et des flèches qui apparaîtront au-dessus de la fenêtre contextuelle.  Pour plus d’informations, consultez [Guide pratique pour afficher et modifier le code avec l’Aperçu de définition (Alt + F12)](how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).

## <a name="go-to-implementation"></a>Accéder à l’implémentation
Naviguer à partir d’un type ou d’une classe de base vers ses implémentations.  S’il existe plusieurs implémentations, elles sont répertoriées dans la fenêtre **Résultats de la recherche de symbole** :

Entrée        | Fonction 
------------ | ---
**Clavier** | Placez le curseur de texte à l’intérieur du nom de type, puis appuyez sur **Ctrl+F12**.
**Souris**    | Cliquez avec le bouton droit sur le nom de type et sélectionnez **Accéder à l’implémentation**.

## <a name="find-all-references"></a>Rechercher toutes les références
Rechercher tous les endroits où une méthode/propriété/variable est utilisée.  Vous pouvez ainsi vérifier l’existence de code mort et les éventuels effets secondaires d’une refactorisation volumineuse.  Appuyez sur **F8** pour basculer d’un résultat à un autre.

Entrée        | Fonction 
------------ | ---
**Clavier** | Placez le curseur de texte à l’intérieur du nom de type, puis appuyez sur **Ctrl+K, R**.
**Souris**    | Cliquez avec le bouton droit sur le nom de type et sélectionnez **Rechercher toutes les références**.

## <a name="navigating-results"></a>Navigation parmi les résultats
Quand vous utilisez les fonctionnalités de navigation de Visual Studio, vous pouvez naviguer vers l’avant et vers l’arrière dans la pile :

Entrée        | Fonction 
------------ | ---
**Ctrl+-**          | Naviguer vers l’arrière dans la pile.
**Ctrl+Maj+-**    | Naviguer vers l’avant de la pile.

Vous pouvez également utiliser les éléments de menu **Affichage > Naviguer vers l’arrière** et **Affichage > Naviguer vers l’avant**.
