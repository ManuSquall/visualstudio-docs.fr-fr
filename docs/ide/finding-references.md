---
title: Recherche de références dans votre code
ms.date: 09/26/2017
ms.topic: conceptual
helpviewer_keywords:
- code editor, find all references
- find all references
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 523ec566e19614951169c184b4796834c4ab0838
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603576"
---
# <a name="find-references-in-your-code"></a>Rechercher des références dans votre code

Vous pouvez utiliser la commande **Rechercher toutes les références** pour savoir où des éléments de code particuliers sont référencés dans tout votre code base. La commande **Rechercher toutes les références** est disponible dans le menu contextuel (clic droit) de l’élément dont vous souhaitez trouver les références. Si vous préférez utiliser le clavier, appuyez sur **Maj+F12**.

Les résultats apparaissent dans une fenêtre Outil nommée **Références \<élément>** , où *élément* est le nom de l’élément qui fait l’objet de la recherche. À partir de la barre d’outils de la fenêtre **Références**, vous pouvez effectuer les opérations suivantes :
- Changer l’étendue de recherche dans une zone de liste déroulante. Vous pouvez choisir d’effectuer la recherche uniquement dans les documents modifiés dans l’ensemble de la solution.
- Copier l’élément référencé sélectionné en choisissant le bouton **Copier**.
- Pour accéder à l’emplacement suivant ou précédent dans la liste, choisissez les boutons appropriés appuyez sur les touches **F8** et **Maj+F8**.
- Supprimer tous les filtres sur les résultats retournés en choisissant le bouton **Effacer tous les filtres**.
- Changer la façon dont les éléments retournés sont regroupés en choisissant un paramètre dans la zone de liste déroulante **Grouper par :** .
- Conserver la fenêtre des résultats de la recherche actuelle en choisissant le bouton **Conserver les résultats**. Les résultats de la recherche actuelle restent alors dans cette fenêtre, et les résultats des nouvelles recherches s’affichent dans une nouvelle fenêtre Outil.
- Rechercher des chaînes dans les résultats de la recherche en entrant du texte dans la zone de texte **Rechercher toutes les références**.

Vous pouvez également placer le pointeur de la souris sur n’importe quel résultat de la recherche pour afficher un aperçu de la référence.

![Fenêtre Outil Rechercher toutes les références](../ide/media/vside_findallreferences.png)

## <a name="navigate-to-references"></a>Accéder à des références
Vous pouvez utiliser les méthodes suivantes pour accéder à des références dans la fenêtre **Références** :

- Appuyez sur **F8** pour accéder à la référence suivante, ou sur **Maj+F8** pour accéder à la référence précédente.
- Appuyez sur la touche **Entrée** sur une référence ou double-cliquez sur la référence pour y accéder dans le code.
- Dans le menu contextuel (clic droit) d’une référence, choisissez les commandes **Accéder à l’emplacement précédent** ou **Accéder à l’emplacement suivant**.
- Choisissez les flèches **Haut** et **Bas** (si elles sont activées dans la boîte de dialogue **Options**). Pour activer cette fonctionnalité, dans la barre de menus, choisissez **Outils** > **Options** > **Environnement** > **Onglets et fenêtres** > **Onglet d’aperçu**, puis cochez les cases **Autoriser l’ouverture des nouveaux fichiers dans l’onglet d’aperçu** et **Afficher les fichiers sélectionnés dans Rechercher les résultats**.

## <a name="change-reference-groupings"></a>Changer les regroupements de références
Par défaut, les références sont regroupées par projet, puis par définition. Toutefois, vous pouvez changer cet ordre de regroupement en changeant le paramètre défini dans la zone de liste déroulante **Grouper par :** de la barre d’outils. Par exemple, vous pouvez changer l’ordre du paramètre par défaut **Projet, puis définition** en **Définition, puis projet**, ainsi que par d’autres paramètres.

**Définition** et **Projet** sont les deux regroupements utilisés par défaut, mais vous pouvez en ajouter d’autres en choisissant la commande **Regroupement** dans le menu contextuel (clic droit) de l’élément sélectionné. Il peut être utile d’ajouter plusieurs regroupements si votre solution contient un grand nombre de fichiers et de chemins.

## <a name="filter-by-reference-type-in-net"></a>Filtrer par type de référence dans .NET
En C# ou Visual Basic, la fenêtre Rechercher des références comporte une colonne de type qui liste le type de référence qu’elle a trouvé. Cette colonne permet de filtrer par type de référence en cliquant sur l’icône de filtre qui s’affiche quand vous pointez sur l’en-tête de colonne. Les références peuvent être filtrées par la lecture, écriture, référence, nom, espace de noms et type.

![Colonne de type dans la fenêtre Rechercher des références ](../ide/media/vside_findallreferencesKind.png)

## <a name="see-also"></a>Voir aussi

- [Navigation dans le code](../ide/navigating-code.md)
