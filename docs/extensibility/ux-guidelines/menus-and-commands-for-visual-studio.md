---
title: Menus et commandes pour Visual Studio (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1f22b7ac4377b600208c079b6af1eff7fc3cbfc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698388"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menus et commandes pour Visual Studio
## <a name="command-usage"></a>Utilisation de commande

### <a name="overview"></a>Vue d'ensemble
 Contrairement à Microsoft Office, qui est une suite qui comprend de nombreux produits distincts, Visual Studio contient de nombreux produits qui contribuent chacun leurs ensembles de commandes à l’IDE Visual Studio global. L’IDE gère la complexité de milliers de commandes en filtrant les fonctionnalités disponibles pour l’utilisateur en fonction du contexte.

 Lorsque le contexte d’un utilisateur change - comme le passage d’une fenêtre de conception à une fenêtre d’édition de code - la fonctionnalité sans rapport avec le nouveau contexte disparaît. Dans le même temps, de nouvelles fonctionnalités apparaissent ainsi que des informations dynamiques connexes, telles que les propriétés et les options Toolbox. L’utilisateur ne doit pas remarquer l’échange de l’ensemble de commande disponible. Si l’utilisateur est distrait ou confus par des commandes apparaissant ou disparaissant, alors la conception de l’interface utilisateur a besoin d’ajustement. Le contexte actuel de l’utilisateur est toujours indiqué d’une ou plusieurs façons, comme dans la barre de titre IDE, la fenêtre Propriétés ou la boîte de dialogue des Pages De propriété.

 Les barres de commande permettent une flexibilité dans l’interface utilisateur. Les seules structures de commande inhérentes à l’environnement Visual Studio sont le menu principal et la barre de commande principale, qui peut à la fois être personnalisé et même caché. D’autres barres de commande apparaissent et disparaissent en fonction de l’état de l’application. Les fenêtres d’outils et les éditeurs de documents peuvent également contenir des barres d’outils intégrées dans leurs bords de fenêtre.

#### <a name="basic-guidelines"></a>Lignes directrices de base

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Utilisez les commandes, les groupes de commande et les menus partagés existants dans la mesure du possible.
 Étant donné que les commandes sont généralement affichées en fonction du contexte, l’utilisation de menus partagés existants et de groupes de commandement garantit que la structure de commande demeure relativement stable entre les changements de contexte. La réutiliser les commandes partagées et le placement de nouvelles commandes à proximité de commandes partagées connexes réduit également la complexité de l’IDE et crée une expérience plus conviviale. Si une nouvelle commande doit être définie, essayez de la placer dans un groupe de commandement partagé existant. Si un nouveau groupe doit être défini, placez-le dans un menu partagé existant à proximité d’un groupe de commandement connexe avant de créer un nouveau menu de haut niveau.

##### <a name="do-not-create-icons-for-every-command"></a>Ne créez pas d’icônes pour chaque commande.
 Réfléchissez bien avant de créer une icône de commande. Les icônes ne doivent être créées que pour les commandes qui :

- apparaissent sur une barre d’outils par défaut.

- sont susceptibles d’être ajoutés par les utilisateurs à une barre d’outils à travers le dialogue **Personnaliser...** .

- avoir une icône associée à la même action dans un autre produit Microsoft.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limiter l’ajout de raccourcis clavier
 La grande majorité des utilisateurs emploient une infime fraction de tous les raccourcis disponibles. En cas de doute, ne liez pas votre fonctionnalité à un raccourci clavier. Travaillez avec votre équipe d’expérience utilisateur avant d’ajouter de nouveaux raccourcis.

##### <a name="give-commands-a-default-menu-placement"></a>Donnez aux commandes un placement par défaut du menu.
 Sachez que vos commandes seront personnalisées par d’autres et concevez-les en conséquence. Il n’y a pas de commande cachée. Toutes les commandes Visual Studio apparaissent dans le dialogue **Tools > Customize,** la fenêtre de commande, auto-complète, les outils > options > dialogue **clavier,** et l’environnement des outils de développement (DTE). Assurez-vous de donner à vos commandes un nom et une pointe d’outils dans votre fichier .ctc afin que les utilisateurs puissent les trouver facilement.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Ne pas dupliquer les commandes partagées sur une barre d’outils intégrée.
 Il est utile de placer des commandes à proximité de la zone de mise au point de l’utilisateur. Une façon de le faire est de créer une barre d’outils intégrée en haut de votre fenêtre d’outil ou éditeur de documents. Les commandes placées sur la barre d’outils doivent être spécifiques à la région de contenu dans la fenêtre. Ne reproduisez pas les commandes partagées sur ces barres d’outils. Par exemple, ne placez jamais une icône « Enregistrer » dans une barre d’outils intégrée.

### <a name="content-and-command-visibility"></a>Visibilité du contenu et de la commande
 Les commandes existent dans les portées suivantes : **Environnement,** **Hiérarchie**et **Document**. Connaître chaque portée afin d’avoir confiance dans le placement de commande.

 Les commandes dans la portée **de l’environnement** établissent le contexte primaire et sont partagées entre plusieurs contextes. Ils modifient la visibilité ou l’arrangement des documents et des fenêtres d’outils. Parmi les commandes dans la portée de l’environnement sont **New Project**, **Connect to Server**, Attach **Process**, **Cut**, **Copy**, **Paste**, **Find**, **Options**, **Personnaliser**, **New Window**, et **Voir l’aide**.

 Les commandes dans la portée **de la hiérarchie** gèrent les hiérarchies dans Visual Studio, y compris le **projet,** **l’équipe**et **les données**. Ils se rapportent au sous-texte d’un projet - par exemple, **Debug**, **Build**, **Test**, **Architecture**, ou **Analyze**. Parmi les commandes dans la portée de la hiérarchie sont **Ajouter un nouvel élément**, New **Query**, **Paramètres de projet**, Ajouter de nouvelles sources de **données**, Assistant de Performance **de lancement**, et **New Diagram**.

 Les commandes de la portée **du document** agissent sur le contenu d’un document, comme le code, la conception ou une requête d’élément de travail (WIQ). Ils agissent également sur la vue d’une fenêtre d’outil ou sont autrement spécifiques à cette fenêtre d’outil. Les commandes de portée des documents agissent également sur les objets de fichier qui sont eux-mêmes spécifiques à la hiérarchie, tels que **Supprimer du projet**. Parmi les commandes dans la portée du document sont **Refactor > renommer**, **Créer une copie de l’élément de travail**, Expand **All**, **Collapse All**, et créer la **tâche utilisateur**.

### <a name="command-placement-decisions"></a>Décisions de placement de commandement
 Une fois que vous avez décidé de créer une commande, vous devrez déterminer son placement approprié et s’il faut créer un raccourci clavier. Suivez cette voie de décision pour déterminer où placer la commande :

 ![Graphique de décision de positionnement de commandes](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Chemin de décision pour le placement de commande dans Visual Studio**

### <a name="command-placement-in-menus"></a>Placement de commande dans les menus

#### <a name="main-menu-bar"></a>Barre de menu principal
 La barre de menu principale devrait être l’emplacement standard pour les commandes de tous les paquets de menu spécifiques au contexte qui contribuent à l’interface utilisateur. La barre de menu principale diffère des autres structures de commande en ce que l’environnement l’utilise pour contrôler quelles commandes sont visibles. Toutes les autres barres de commande désactivent simplement les commandes qui sont hors contexte, qu’elles soient placées sur un menu ou sur une barre d’outils.

 L’environnement définit un ensemble de commandes intégrées dans la barre de menu principale qui sont courantes dans l’ensemble de l’IDE et de multiples domaines de tâches. Ces commandes sont toujours visibles, quels que soient les VSPackages chargés dans l’environnement. Bien que VSPackages puisse étendre cet ensemble de commandes, l’ensemble de commandes de chaque produit et le placement de leurs commandes relèvent de chaque équipe.

 La structure du menu principal Visual Studio peut être divisée en catégories de menus suivants :

##### <a name="core-menus"></a>Menus de base

- Fichier

- Modifier

- Vue

- Outils

- Fenêtre

- Aide

##### <a name="project-specific-menus"></a>Menus spécifiques au projet

- Projet

- Générer

- Débogage

##### <a name="context-specific-menus"></a>Menus spécifiques au contexte

- Équipe

- Données

- Test

- Architecture

- Analyser

##### <a name="document-specific-menus"></a>Menus spécifiques aux documents

- Format

- Table de charge de travail

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Lors de la conception des menus principaux, respectez ces règles :

- Ne dépassez pas 25 éléments de haut niveau dans un contexte donné

- Les menus ne doivent jamais dépasser 600 pixels de hauteur.

- Évaluez un menu principal dans plusieurs contextes, comme dans l’Ultimate SKU et le Profil Général.

- Les menus Flyout sont acceptables.

- Les menus Flyout doivent contenir au moins trois articles et pas plus de sept.

- Les menus flyout ne devraient aller qu’à un niveau de profondeur - certains éléments du menu Visual Studio ont sous-genre en cascade, mais ce modèle n’est pas encouragé.

- N’utilisez pas plus de six séparateurs. Les regroupements doivent adhérer à l’illustration suivante :

     ![Instructions pour le regroupement du menu principal](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-b_MainMenus")

- Bien qu’il ne soit pas nécessaire d’avoir chaque groupe dans le chiffre, l’ajout de groupes supplémentaires est limité.

- Chaque groupe doit avoir de deux à sept éléments de menu.

#### <a name="main-menu-ordering"></a>Commande de menu principal
 Avant d’ajouter un nouvel article de haut niveau, envisagez de placer la commande dans un menu de haut niveau existant. Lors de l’ajout d’un nouveau menu de haut niveau, assurez-vous de le placer à l’emplacement correct. Décidez si le menu est spécifique au projet, au contexte ou au document. Gardez le nom du menu de haut niveau concis et n’utilisez qu’un seul mot.

 Les menus de base doivent réserver le reste des commandes. Fichier, Modifier et Afficher doit toujours être à gauche, et les outils, la fenêtre et l’aide doivent toujours être à droite.

#### <a name="context-menus"></a>Menu contextuels
 Placer trop de fonctionnalités dans les menus contextuels se traduit par une interface difficile à apprendre. Toutes les fonctionnalités majeures doivent être disponibles via la barre de menu principal. Le placement des commandes doit être concilié avec les commandes existantes afin d’éviter les commandes en double. Pour les menus contextuels, la coque définit les groupes de menu standard qui doivent être inclus selon que le menu contextuel est pour la solution, un nœud de projet, ou un élément de projet.

 Lors de la conception des menus contextuels, respectez les mêmes règles que pour le menu principal, et en plus :

- Ne dépassez pas 25 éléments de menu de haut niveau.

- Les menus flyout sont acceptables mais ne doivent pas dépasser un niveau de profondeur - ne jamais utiliser des flyouts en cascade.

- N’utilisez pas plus de six séparateurs.

### <a name="command-placement-in-toolbars"></a>Placement de commande dans les barres d’outils

#### <a name="general-toolbars"></a>Barres d’outils générales
 Lors de la conception et de l’organisation des barres d’outils, suivez ces normes :

- N’utilisez pas plus d’un verbe par bouton. Un bouton et une action.

- Utilisez le texte à côté de l’icône uniquement s’il doit être renforcé avec l’étiquette.

- Utilisez une boîte combo exclusivement pour les propriétés qui seront commutées plusieurs fois en une seule session. Sinon, exposez la propriété ailleurs.

- La largeur d’une boîte de combo doit égaler la largeur de l’élément le plus long dans la boîte - 30%. Par exemple, si l’élément le plus long est de 200 pixels, alors la boîte combo doit être de 260 pixels de large.

- Limitez l’utilisation des séparateurs. L’utilisation d’un séparateur à côté d’un décrochage est un anti-modèle, parce que la forme de la chute elle-même agit comme un séparateur visuel.

- Les groupes d’icônes doivent contenir de trois à six icônes.

- Si les qualifications donnent lieu à plusieurs commandes utiles, utilisez un bouton split qui stocke le dernier paramètre :

     ![Boutons Fractionner dans Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")

     **Exemple d’un bouton fendu. Les six commandes sur la gauche peuvent plutôt s’insérer dans un seul bouton.**

#### <a name="product-specific-toolbars"></a>Barres d’outils spécifiques aux produits
 Chaque produit peut fournir une barre d’outils par défaut qui contient des commandes fréquemment utilisées et importantes, et la barre d’outils par défaut de chaque produit doit apparaître la première fois que Visual Studio est lancé après l’installation du produit.

 Les produits devraient également tirer parti des groupes de commandement partagés et des menus fournis par l’IDE. Chaque groupe de commande partagé est placé dans un menu partagé destiné à organiser les commandes connexes d’une manière significative pour l’utilisateur. Il est important de tirer parti de cette structure de commandement partagée afin de réduire la complexité.

#### <a name="global-toolbars"></a>Barres d’outils mondiales
 Les barres d’outils globales sont nécessaires pour s’adapter sur une rangée dès la sortie de la boîte. Lors de la création d’une nouvelle barre d’outils globale, suivez les lignes directrices pour ce type de barre d’outils.

 **Lignes directrices générales sur les barres d’outils :**

- Chaque barre d’outils a 24 pixels dans les contrôles communs (gripper, débordement).

- Chaque bouton de barre d’outils est de 22 pixels de large, y compris le rembourrage. Faire de l’icône un bouton fendu ajoute 11 pixels de largeur de plus.

- La duplication des commandes à travers les barres d’outils est autorisée.

  **Les barres d’outils spécifiques aux documents** apparaissent lorsqu’un certain type de fichier est actif et disparaissent lorsqu’un type de fichier différent devient actif.

- Les barres d’outils spécifiques aux documents peuvent ne pas avoir plus de 12 boutons.

- La largeur totale de la barre d’outils ne peut pas dépasser 300 pixels.

- Chaque type de fichier peut avoir soit une barre d’outils intégrée ou une barre d’outils globale spécifique à un document, mais pas les deux.

  **Les barres d’outils spécifiques au contexte** apparaissent lorsqu’un certain contexte est défini et ont tendance à rester actives pendant de longues périodes.

- La limite de bouton pour toutes les barres d’outils spécifiques au contexte est de 18.

- Si la plupart des utilisateurs n’utilisent pas systématiquement les commandes de cette barre d’outils lorsque le contexte est actif, alors n’associez pas cette barre d’outils à un contexte.

- Assurez-vous que la barre d’outils disparaît en sortant du contexte. Aucune de ces barres d’outils ne devrait apparaître sur le démarrage.

  **Les barres d’outils sans contexte n’apparaissent** jamais automatiquement. Ceux-ci ne s’affichent que lorsque l’utilisateur les active. Gardez la largeur maximale en dessous de 200 pixels.

### <a name="general-organization-and-shell-defined-groups"></a>Organisation générale et groupes définis par les coquilles
 Utilisez les commandes, les groupes de commande et les menus partagés existants. Si une nouvelle commande doit être définie, essayez de la placer dans un groupe de commandement partagé existant. Si un nouveau groupe doit être défini, essayez de le placer dans un menu partagé existant à proximité d’un groupe de commandement connexe avant de créer un nouveau menu de haut niveau. Cela réduit la complexité des commandes tout en assurant un placement de commande uniforme dans l’IDE.

 Le menu **Format** partagé, généralement indiqué dans le contexte des fenêtres de documents de style designer, est illustré dans l’image suivante :

 ![Menu Format Visual Studio avec légendes](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")

 **Groupes de menu en studio visuel**

### <a name="reducing-and-reusing-commands"></a>Réduire et réutiliser les commandes
 Les commandes sont généralement affichées en fonction du contexte, afin de réduire le nombre de commandes que l’utilisateur voit à un moment donné. Toutefois, vous devez également réutiliser les menus partagés existants et les groupes de commandement pour vous assurer que la structure de commandement demeure relativement stable entre les changements de contexte.

 La réutiliser les commandes partagées et le placement de nouvelles commandes à proximité de commandes partagées connexes réduit la complexité de l’IDE et crée une expérience plus conviviale.

## <a name="naming-commands"></a>Désignation des commandes

### <a name="naming-conventions"></a>Conventions d'attribution d'un nom
 Le nom de commande cohérent est essentiel afin que les utilisateurs puissent trouver et exécuter des commandes, soit en utilisant la ligne de commande ou en liant à un raccourci de clavier. Les noms de commande aident également l’utilisateur à comprendre à quel but une commande sert lorsqu’elle est affichée sur une barre d’outils ou dans un menu en cascade ou en contexte.

#### <a name="when-naming-commands"></a>Lors de la désignation des commandes:

- Construisez le texte pour qu’il soit facilement localisable. Pour en savoir plus sur la localisation du texte, voir [Les meilleures pratiques de localisation](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices).

- Sois concis. Les commandes ne doivent pas utiliser plus de trois mots.

- Utiliser la majuscule des cas de titre : la première lettre de chaque mot doit être capitalisée. Pour plus d’informations sur le formatage de texte dans Visual Studio, voir [style texte](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

- Prenez en considération l’endroit où la commande sera placée. Est-ce dans un menu de haut niveau ou un flyout? Par exemple, lors du regroupement des commandes d’alignement dans un survol, la commande de haut niveau doit être "Align" et les commandes de survol doivent être "gauche", "droite", "Centre", "Justifier," et ainsi de suite. Il serait redondant de nommer les commandes de vol "Align Left" ou "Align Right".

     ![Menu Format Visual Studio](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>Utilisation d’icônes avec des commandes
 Soyez épargnant dans l’utilisation de l’appariement d’icônes avec des commandes. Bien que l’association d’une image unique avec une commande accélère la capacité de l’utilisateur à identifier cette commande, l’encombrement visuel et l’inefficacité se produisent avec la surutilisation de l’image. Les règles suivantes aident à décider de créer ou non une icône de commande.

#### <a name="use-an-icon-with-a-command-only-if"></a>Utilisez une icône avec une commande uniquement si :

- La même commande a une icône qui lui est associée dans un autre produit Microsoft de premier plan, comme l’une des applications Microsoft Office.

- La commande sera placée dans une barre d’outils par défaut.

- La commande est une commande spécialisée que les utilisateurs sont susceptibles d’ajouter à une barre d’outils en utilisant le **dialogue "Customize...".**

## <a name="access-and-shortcut-keys"></a>Accès et clés de raccourci

### <a name="overview"></a>Vue d'ensemble
 Il existe deux types d’affectations de touches de clavier :

- **Les touches d’accès** (également connues sous le nom d’accélérateurs) permettent l’accès au clavier via les menus de commande et à chaque étiquette dans l’interface utilisateur de dialogue. Les clés d’accès sont principalement à des fins d’accessibilité, sont attribuées à tous les menus et la plupart des contrôles de boîte de dialogue, ne sont pas destinés à être mémorisés, affectent seulement la fenêtre actuelle, et sont localisés.

- **Les touches de raccourci** utilisent principalement les séquences clés Control (Ctrl) et Function (Fn). Ils sont conçus davantage pour les utilisateurs avancés et l’aide à la productivité. Ils ne sont affectés qu’aux commandes les plus souvent utilisées et permettent un accès rapide tout en contournant le menu principal. Les clés de raccourci sont destinées à être mémorisées, et pour cette raison doivent être attribuées conformément au schéma de profil. Les schémas de clés de raccourci peuvent varier d’un profil à l’autre. Un utilisateur peut personnaliser les touches de raccourci grâce à **Tools > Options > Clavier**.

### <a name="assigning-access-keys"></a>Attribution des clés d’accès
 Les touches d’accès se composent d’Alt plus de clé alphanumérique(s). Attribuez une clé d’accès à chaque élément de menu sans exception. Suivez Windows et les conventions communes pour l’attribution des clés d’accès. par exemple, la clé d’accès pour **File > New** devrait toujours être **Alt, F, N**.

 N’utilisez pas de lettres à largeur d’un pixel comme «i» (en majuscules ou minuscules) ou un «l» minuscule et évitez d’utiliser des caractères avec des descendants (g, j, p, q, et y) car ceux-ci sont difficiles à distinguer.

 Évitez d’utiliser des touches en double lorsque c’est possible. Dans les cas où la duplication est inévitable, le système de menu gère les conflits en faisant du vélo à travers toutes les commandes qui utilisent la clé. Par exemple, pour une hypothétique commande "Number" sous le menu Fichier qui reproduit la clé d’accès "N", **Alt, F, N** créerait un nouveau fichier, et **Alt, F, N, N** effectuerait la commande "Numéro".

### <a name="assigning-shortcut-keys"></a>Attribution des clés de raccourci
 Évitez d’attribuer de nouvelles clés de raccourci, car elles ne sont pas nécessaires pour chaque commande et taxe du système (et mémoire utilisateur) si elle est surutilisée. Les données du Programme d’amélioration de l’expérience client (CEIP) indiquent que les utilisateurs de Visual Studio n’utilisent qu’un petit sous-ensemble des raccourcis intégrés.

 Lors de la définition des raccourcis, suivez ces règles :

- **Utilisez des séquences clés Control (Ctrl) et Function (Fn).**

- **Préserver les raccourcis fréquemment utilisés.** Maintenir les raccourcis les plus populaires.

- **Facilitez le type des raccourcis d’éditeur.** Lier des raccourcis faciles à taper aux commandes dont les développeurs ont le plus besoin lors de la rédaction du code. Par exemple, **Edit.InvokeSmartTag** doit avoir une clé de raccourci rapide comme CtrlMD/ et non Alt-Shift-F10.

- **Efforcez-vous de raccourcis à thème constant.**

- **Suivez les directives de Windows pour déterminer les clés modificateures à utiliser.** Utilisez des combinaisons de clés Ctrl pour les commandes qui ont des effets à grande échelle, tels que des commandes qui s’appliquent à un document entier. Utilisez des combinaisons de clés Shift pour les commandes qui prolongent ou complètent les actions de la clé de raccourci standard. N’utilisez pas de combinaisons Ctrl-Alt.

- **Retirer les raccourcis extrasons.** Si vous avez une caractéristique héritée, envisagez de supprimer les raccourcis utilisés avec une extrême rareté (moins de 10 fois des données du CEIP) ou une rareté modérée (moins de 100 fois des données du CEIP) si une clé d’accès permet un accès rapide à la même commande. Par exemple : Alt, H, C ouvriront Help/Contents.

  Il n’y a pas de moyen simple de vérifier la disponibilité des raccourcis. Si vous souhaitez ajouter un raccourci, suivez ces étapes :

1. Consultez la liste des [raccourcis Visual Studio 2013](http://visualstudioshortcuts.com/2013/) pour déterminer s’il existe des commandes similaires pour regrouper les vôtres.

2. Rendez-vous sur **Tools > Options > Environnement > Clavier** et testez votre raccourci. Vérifiez chaque schéma de cartographie du clavier énuméré dans le cadre du programme de cartographie du clavier supplémentaire suivant. Vérifiez les profils Général, C, VB et CMD, car ceux-ci partagent des raccourcis uniques. Votre raccourci est disponible s’il n’est pas cartographié dans l’un de ces endroits.
