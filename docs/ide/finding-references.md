---
title: Recherche de références dans votre code
ms.date: 09/26/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- code editor, find all references
- find all references
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 143a40c1a2e3602460419465cb84d6ffa44d853c
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269850"
---
# <a name="find-references-in-your-code"></a>Rechercher des références dans votre code

Vous pouvez utiliser la commande **Rechercher toutes les références** pour savoir où des éléments de code particuliers sont référencés dans tout votre code base. La commande **Rechercher toutes les références** est disponible dans le menu contextuel (clic droit) de l’élément dont vous souhaitez trouver les références. Si vous préférez utiliser le clavier, appuyez sur **Maj+F12**.

Les résultats s’affichent dans une fenêtre Outil nommée **Références <element>**, où *element* est le nom de l’élément qui fait l’objet de la recherche. À partir de la barre d’outils de la fenêtre **Références**, vous pouvez effectuer les opérations suivantes :
- Changer l’étendue de recherche dans une zone de liste déroulante. Vous pouvez choisir d’effectuer la recherche uniquement dans les documents modifiés dans l’ensemble de la solution.
- Copier l’élément référencé sélectionné en choisissant le bouton **Copier**.
- Pour accéder à l’emplacement suivant ou précédent dans la liste, choisissez les boutons appropriés appuyez sur les touches **F8** et **Maj+F8**.
- Supprimer tous les filtres sur les résultats retournés en choisissant le bouton **Effacer tous les filtres**.
- Changer la façon dont les éléments retournés sont regroupés en choisissant un paramètre dans la zone de liste déroulante **Grouper par :**.
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

## <a name="see-also"></a>Voir aussi

- [Navigation dans le code](../ide/navigating-code.md)