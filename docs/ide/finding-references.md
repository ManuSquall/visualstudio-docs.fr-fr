---
title: Recherche de références dans votre code
ms.date: 09/26/2017
ms.topic: conceptual
helpviewer_keywords:
- code editor, find all references
- find all references
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e4ef16ef88e871778fd4e0c755ffb156c374109
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592033"
---
# <a name="find-references-in-your-code"></a>Rechercher des références dans votre code

Vous pouvez utiliser la commande **Rechercher toutes les références** pour savoir où des éléments de code particuliers sont référencés dans tout votre code base. La commande **Rechercher toutes les références** est disponible dans le menu contextuel (clic droit) de l’élément dont vous souhaitez trouver les références. Si vous préférez utiliser le clavier, appuyez sur **Maj+F12**.

Les résultats apparaissent dans une fenêtre d’outil nommée ** \<élément> références,** où l’élément est le nom de l’élément que vous recherchez. *element* À partir de la barre d’outils de la fenêtre **Références**, vous pouvez effectuer les opérations suivantes :
- Changer l’étendue de recherche dans une zone de liste déroulante. Vous pouvez choisir d’effectuer la recherche uniquement dans les documents modifiés dans l’ensemble de la solution.
- Copier l’élément référencé sélectionné en choisissant le bouton **Copier**.
- Pour accéder à l’emplacement suivant ou précédent dans la liste, choisissez les boutons appropriés appuyez sur les touches **F8** et **Maj+F8**.
- Supprimer tous les filtres sur les résultats retournés en choisissant le bouton **Effacer tous les filtres**.
- Modifier la façon dont les éléments retournés sont regroupés en choisissant un paramètre dans le **Groupe par :** boîte de liste d’abandon.
- Conserver la fenêtre des résultats de la recherche actuelle en choisissant le bouton **Conserver les résultats**. Les résultats de la recherche actuelle restent alors dans cette fenêtre, et les résultats des nouvelles recherches s’affichent dans une nouvelle fenêtre Outil.
- Rechercher des chaînes dans les résultats de la recherche en entrant du texte dans la zone de texte **Rechercher toutes les références**.

Vous pouvez également placer le pointeur de la souris sur n’importe quel résultat de la recherche pour afficher un aperçu de la référence.

![Fenêtre Outil Rechercher toutes les références](../ide/media/vside_findallreferences.png)

## <a name="navigate-to-references"></a>Accéder à des références
Vous pouvez utiliser les méthodes suivantes pour accéder à des références dans la fenêtre **Références** :

- Appuyez sur **F8** pour accéder à la référence suivante, ou sur **Maj+F8** pour accéder à la référence précédente.
- Appuyez sur la touche **Entrée** sur une référence ou double-cliquez sur la référence pour y accéder dans le code.
- Dans le menu contextuel (clic droit) d’une référence, choisissez les commandes **Accéder à l’emplacement précédent** ou **Accéder à l’emplacement suivant**.
- Choisissez les touches **Up Arrow** et **Down Arrow** (si elles sont activées dans la boîte de dialogue **Options).** Pour activer cette fonctionnalité, sur la barre du menu, choisissez des**onglets** > **d’environnement d’options** >  > **d’outils** > et**l’onglet**Windows Preview, puis sélectionnez les **nouveaux fichiers Allow à ouvrir dans l’onglet aperçu** et **prévisualiser les fichiers sélectionnés dans les** boîtes Trouver des résultats. **Tools**

## <a name="change-reference-groupings"></a>Changer les regroupements de références
Par défaut, les références sont regroupées par projet, puis par définition. Toutefois, vous pouvez changer cet ordre de regroupement en changeant le paramètre défini dans la zone de liste déroulante **Grouper par :** de la barre d’outils. Par exemple, vous pouvez changer l’ordre du paramètre par défaut **Projet, puis définition** en **Définition, puis projet**, ainsi que par d’autres paramètres.

**Définition** et **Projet** sont les deux regroupements utilisés par défaut, mais vous pouvez en ajouter d’autres en choisissant la commande **Regroupement** dans le menu contextuel (clic droit) de l’élément sélectionné. Il peut être utile d’ajouter plusieurs regroupements si votre solution contient un grand nombre de fichiers et de chemins.

## <a name="filter-by-reference-type-in-net"></a>Filtrer par type de référence dans .NET
En C# ou Visual Basic, la fenêtre Rechercher des références comporte une colonne de type qui liste le type de référence qu’elle a trouvé. Cette colonne permet de filtrer par type de référence en cliquant sur l’icône de filtre qui s’affiche quand vous pointez sur l’en-tête de colonne. Les références peuvent être filtrées par la lecture, écriture, référence, nom, espace de noms et type.

![Colonne de type dans la fenêtre Rechercher des références ](../ide/media/vside_findallreferencesKind.png)

## <a name="see-also"></a>Voir aussi

- [Code de navigation](../ide/navigating-code.md)
