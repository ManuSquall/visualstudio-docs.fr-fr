---
title: "Personnalisation de l’IDE | Microsoft Docs"
description: "Visual Studio pour Mac peut être personnalisé de plusieurs façons, permettant aux utilisateurs de développer des applications dans un environnement qui répond à leurs besoins en matière d’efficacité et d’esthétique. Cette rubrique explore les différentes façons dont Visual Studio pour Mac peut être adapté à vos besoins."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: F7C2A28C-0759-4E0D-A28E-B72D5AB73DB6
ms.openlocfilehash: bbc2f70f0d6774269f481cad5571dd9b78bac2da
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="customizing-the-ide"></a>Personnalisation de l’IDE

Visual Studio pour Mac peut être personnalisé de plusieurs façons, permettant aux utilisateurs de développer des applications dans un environnement qui répond à leurs besoins en matière d’efficacité et d’esthétique. Cet article explore les différentes façons dont Visual Studio pour Mac peut être adapté à vos besoins.

## <a name="dark-theme"></a>Thème foncé

![Vue du thème foncé](media/customizing-the-ide-image7a.png)

Vous pouvez basculer entre les thèmes de Visual Studio pour Mac en accédant à **Visual Studio > Préférences... > Environnement > Style visuel** et en sélectionnant le thème de votre choix dans la liste déroulante **Thème de l’interface utilisateur**, comme illustré dans l’image suivante :

 ![Sélection du thème foncé](media/customizing-the-ide-image7b.png)

## <a name="localization"></a>Localisation

Visual Studio pour Mac est localisé dans les 13 langues suivantes, ce qui lui permet d’être accessible à un plus grand nombre de développeurs :

* Chinois - Chine
* Chinois - Taïwan
* Tchèque
* Français
* Allemand
* Anglais
* Italien
* Japonais
* Coréen
* Portugais - Brésil
* Russe
* Espagnol
* Turc

Pour changer la langue affichée par Visual Studio pour Mac, accédez à **Visual Studio > Préférences... > Environnement > Style visuel** et sélectionnez la langue de votre choix dans la liste déroulante **Langue de l’interface utilisateur**, comme illustré dans l’image suivante :


![Sélection de la langue](media/customizing-the-ide-image11a.png)

## <a name="author-information"></a>Informations sur l’auteur

Le panneau d’informations sur l’auteur vous permet d’ajouter des informations pertinentes sur vous-même, comme votre nom, votre adresse de messagerie, le propriétaire du copyright de votre travail, votre entreprise et la marque déposée :

 ![Modifier la section Informations sur l’auteur](media/customizing-the-ide-image9a.png)

Ces informations sont utilisées pour remplir les en-têtes de fichier standard, par exemple une licence, que vous pouvez ajouter aux nouveaux fichiers :

 ![Options d’en-tête standard](media/customizing-the-ide-image8a.png)


Les champs **Nom** et **E-mail** sont utilisés dans les validations effectuées via la gestion de versions dans Visual Studio pour Mac. Si vous n’avez pas rempli ces champs, Visual Studio pour Mac vous invite à le faire quand vous essayez d’utiliser la gestion des versions.

## <a name="key-bindings"></a>Combinaisons de touches

Les combinaisons de touches vous permettent d’adapter votre environnement de développement afin de vous déplacer plus efficacement dans Visual Studio pour Mac. Il fournit des combinaisons de touches courantes dans de nombreux IDE répandus, comme Visual Studio (Windows), ReSharper, Visual Studio Code et Xcode.

Les combinaisons de touches peuvent être définies en accédant à **Visual Studio > Préférences... > Environnement > Combinaisons de touches**, comme illustré dans l’image suivante :

 ![Définir des combinaisons de touches](media/customizing-the-ide-image10a.png)

À partir d’ici, vous pouvez rechercher des combinaisons de touches, afficher les combinaisons en conflit, ajouter de nouvelles combinaisons et modifier les combinaisons existantes.

## <a name="workspace-layout"></a>Disposition de l'espace de travail

L’espace de travail de Visual Studio pour Mac se compose d’une zone de document principale (normalement l’éditeur, l’aire du concepteur ou le fichier d’options), entourée de *panneaux* complémentaires, qui contiennent des informations utiles pour l’accès et la gestion des fichiers d’application, pour le test et pour le débogage.

 ![Disposition de l'espace de travail](media/customizing-the-ide-image1a.png)

### <a name="viewing-and-arranging-pads"></a>Affichage et organisation des panneaux

Quand vous ouvrez une nouvelle solution ou un nouveau fichier dans Visual Studio pour Mac, vous pouvez noter la présence de certains *panneaux* dans l’espace de travail, notamment le panneau Solution, Structure du document et Erreurs :

![Panneaux Solution](media/customizing-the-ide-image2a.png)

Visual Studio pour Mac fournit des panneaux contenant des informations supplémentaires, des outils et des aides à la navigation, tous accessibles en sélectionnant l’élément de menu **Afficher > Panneaux** et en choisissant un panneau à ajouter :

 ![Sélectionner un nouveau panneau](media/customizing-the-ide-image3a.png)

Les panneaux peuvent aussi être ouverts automatiquement par différentes commandes, comme la commande **Rechercher dans les fichiers** (Maj+Cmd+F), qui ouvre un panneau flottant avec les résultats de la recherche.

Les panneaux peuvent être déplacés et organisés tout au long de votre flux de travail, de la façon la plus pratique pour vous. Par exemple, ils peuvent être ancrés sur n’importe quel côté de l’éditeur de document, adjacents à un autre panneau, au-dessus ou en dessous d’un autre panneau ou sous la forme d’un ensemble de panneaux à onglets qui vous permettent de passer rapidement de l’un à l’autre.

Pour les panneaux fréquemment utilisés, vous pouvez également les détacher entièrement de la fenêtre de Visual Studio pour Mac et créer une fenêtre distincte pour ces panneaux.

Les panneaux peuvent être masqués et fermés grâce aux commandes de bascule situées dans le coin supérieur droit de chaque panneau :

![Masquage et fermeture des panneaux](media/customizing-the-ide-image5a.png)

Les panneaux masqués automatiquement sont ancrés sur les côtés de l’espace de travail, ce qui les rend facilement accessibles quand ils sont nécessaires. Le fait de passer le pointeur de la souris sur le panneau l’affiche à nouveau, et il redevient masqué dès que la souris et le focus du clavier le quittent.


### <a name="organizing-layouts"></a>Organisation des dispositions

Les panneaux qui sont affichés à un moment donné dépendent du contexte actif. Par exemple, quand vous utilisez le concepteur visuel, les panneaux des outils et de la grille de propriétés sont les plus importants ; lors du débogage, il est pratique d’avoir les panneaux du débogueur pour afficher la pile et les variables locales.

L’état des panneaux ouverts est représenté par une *disposition*. Vous pouvez changer les dispositions manuellement via le menu Affichage, comme illustré dans l’image suivante, ou elles changent elles-mêmes automatiquement quand vous exécutez une action, comme déboguer ou ouvrir un fichier Storyboard :

![Sélection de nouvelles dispositions](media/customizing-the-ide-image6b.png)

Il n’existe qu’une seule disposition active à un moment donné, et toute modification apportée à une disposition, comme ajouter ou repositionner un panneau, change seulement la disposition active. Quand vous fermez Visual Studio pour Mac, les modifications que vous avez apportées ne seront pas enregistrées.


Cependant, il est possible de créer une nouvelle disposition en utilisant l’élément de menu **Afficher > Enregistrer la disposition active...**. Ceci ajoute votre disposition actuelle au menu et vous permet de la sélectionner à tout moment :

![Enregistrer la disposition active](media/customizing-the-ide-image6a.png)

### <a name="side-by-side-editing-support"></a>Prise en charge de l’édition côte à côte

Visual Studio pour Mac vous permet d’ouvrir des éditeurs de texte côte à côte, ou d’avoir un éditeur dans une fenêtre flottante détachée.

Le mode 2 colonnes peut être activé via l’élément de menu Afficher, en sélectionnant **Afficher > Colonnes de l’éditeur > 2 colonnes**, ou en faisant glisser l’onglet d’un éditeur sur un des bords de la zone de l’éditeur :

 ![Mode deux colonnes côte à côte](media/customizing-the-ide-sbs.png)

Les onglets de l’éditeur peuvent être déplacés en dehors de la zone du document pour créer une fenêtre d’éditeur flottante. Cette fenêtre flottante prend aussi en charge les éditeurs côte à côte et peut contenir plusieurs onglets d’éditeur :

 ![Créer une fenêtre](media/customizing-the-ide-sbs1.png)

 ![Deux colonnes côte à côte avec des onglets supplémentaires](media/customizing-the-ide-sbs2.png)

Pour revenir à un seul éditeur ouvert, sélectionnez **Afficher > Colonnes de l’éditeur > 1 colonne**.
