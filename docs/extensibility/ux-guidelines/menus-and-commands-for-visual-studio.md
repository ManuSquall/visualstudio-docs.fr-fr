---
title: Menus et commandes pour Visual Studio | Microsoft Docs
description: Découvrez comment les barres de commandes offrent une certaine flexibilité dans l’interface utilisateur lorsque vous créez de nouvelles fonctionnalités pour Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ef66123e1a4d62f89fc1c69b81bcb780d0b294f0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902096"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menus et commandes pour Visual Studio
## <a name="command-usage"></a>Utilisation de la commande

### <a name="overview"></a>Vue d’ensemble
 Contrairement à Microsoft Office, qui est une suite comprenant de nombreux produits distincts, Visual Studio contient de nombreux produits qui contribuent chacun à l’IDE Visual Studio. L’IDE gère la complexité des milliers de commandes en filtrant les fonctionnalités disponibles pour l’utilisateur en fonction du contexte.

 Lorsque le contexte d’un utilisateur change, par exemple en passant d’une fenêtre de conception à une fenêtre d’édition de code, les fonctionnalités non liées au nouveau contexte disparaissent. En même temps, de nouvelles fonctionnalités regroupent les informations dynamiques associées, telles que les propriétés et les options de la boîte à outils. L’utilisateur ne doit pas remarquer la permutation du jeu de commandes disponible. Si l’utilisateur est distrait ou non par des commandes qui apparaissent ou disparaissent, la conception de l’interface utilisateur doit être ajustée. Le contexte actuel de l’utilisateur est toujours indiqué d’une ou de plusieurs façons, par exemple dans la barre de titre de l’IDE, la Fenêtre Propriétés ou la boîte de dialogue pages de propriétés.

 Les barres de commandes offrent une certaine flexibilité dans l’interface utilisateur. Les seules structures de commande inhérentes à l’environnement Visual Studio sont le menu principal et la barre de commandes principale, qui peuvent être personnalisés et même masqués. D’autres barres de commandes apparaissent et disparaissent en fonction de l’état de l’application. Les fenêtres outil et les éditeurs de documents peuvent également contenir des barres d’outils incorporées dans leurs bords de fenêtre.

#### <a name="basic-guidelines"></a>Instructions de base

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Utilisez dans la mesure du possible les commandes partagées, les groupes de commandes et les menus existants.
 Étant donné que les commandes sont généralement affichées en fonction du contexte, l’utilisation de menus et de groupes de commandes partagés existants garantit que la structure de la commande reste relativement stable entre les modifications en contexte. La réutilisation des commandes partagées et le placement de nouvelles commandes proches des commandes partagées associées réduit également la complexité de l’IDE et facilitent l’utilisation de l’interface utilisateur. Si vous devez définir une nouvelle commande, essayez de la placer dans un groupe de commandes partagé existant. Si un nouveau groupe doit être défini, placez-le dans un menu partagé existant à proximité d’un groupe de commandes associé avant de créer un menu de niveau supérieur.

##### <a name="do-not-create-icons-for-every-command"></a>Ne créez pas d’icônes pour chaque commande.
 Réfléchissez bien avant de créer une icône de commande. Les icônes ne doivent être créées que pour les commandes suivantes :

- apparaît dans une barre d’outils par défaut.

- sont susceptibles d’être ajoutés par les utilisateurs à une barre d’outils via la boîte de dialogue **personnaliser...** .

- avoir une icône associée à la même action dans un autre produit Microsoft.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limiter l’ajout de raccourcis clavier
 La grande majorité des utilisateurs utilisent une petite fraction de tous les raccourcis disponibles. En cas de doute, ne liez pas votre fonctionnalité à un raccourci clavier. Collaborez avec l’équipe de l’expérience utilisateur avant d’ajouter de nouveaux raccourcis.

##### <a name="give-commands-a-default-menu-placement"></a>Donnez aux commandes un emplacement de menu par défaut.
 N’oubliez pas que vos commandes sont personnalisées par d’autres et que vous les concevez en conséquence. Il n’existe pas de commande masquée. Toutes les commandes Visual Studio s’affichent dans la boîte de dialogue **outils > personnalisation** , la fenêtre commande, la saisie semi-automatique, la boîte de dialogue **outils > options > clavier** et l’environnement des outils de développement (DTE). Veillez à donner un nom et une info-bulle à vos commandes dans votre fichier. CTC afin que les utilisateurs puissent les trouver facilement.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Ne dupliquez pas les commandes partagées dans une barre d’outils incorporée.
 Il est utile de placer les commandes à proximité de la zone du focus de l’utilisateur. Pour ce faire, vous pouvez créer une barre d’outils incorporée en haut de la fenêtre outil ou de l’éditeur de document. Les commandes placées dans la barre d’outils doivent être spécifiques à la région de contenu dans la fenêtre. Ne dupliquez pas les commandes partagées sur ces barres d’outils. Par exemple, ne placez jamais l’icône « Enregistrer » dans une barre d’outils incorporée.

### <a name="content-and-command-visibility"></a>Visibilité du contenu et de la commande
 Les commandes existent dans les étendues suivantes : **environnement**, **hiérarchie** et **document**. Identifiez chaque étendue pour avoir confiance dans le positionnement de la commande.

 Les commandes dans la portée de l' **environnement** établissent le contexte principal et sont partagées entre plusieurs contextes. Ils modifient la visibilité ou la disposition des documents et des fenêtres outil. Parmi les commandes dans l’étendue de l’environnement se trouvent les **nouveaux projets**, **se connectent au serveur**, **attachent le processus**, **coupez**, **copie**, **collent**, **recherche**, **options**, **personnaliser**, **nouvelle fenêtre** et **afficher l’aide**.

 Les commandes dans l’étendue de la **hiérarchie** gèrent les hiérarchies dans Visual Studio, y compris le **projet**, l' **équipe** et les **données**. Ils se rapportent au sous-contexte d’un projet, par exemple, **Déboguer**, **générer**, **Tester**, **architecture** ou **analyser**. Parmi les commandes de l’étendue de la hiérarchie se trouvent les commandes **Ajouter un nouvel élément**, **nouvelle requête**, **paramètres du projet**, **Ajouter une nouvelle source de données**, lancer l' **Assistant Performance** et **nouveau diagramme**.

 Les commandes dans l’étendue du **document** agissent sur le contenu d’un document, tel que le code, la conception ou une requête d’élément de travail (wiq). Ils agissent également sur la vue d’une fenêtre outil ou sont spécifiques à cette fenêtre outil. Les commandes d’étendue de document agissent également sur les objets de fichier qui sont eux-mêmes des hiérarchies spécifiques à la hiérarchie, tels que **supprimer du projet**. Parmi les commandes dans l’étendue du document, vous pouvez **refactoriser > renommer**, **créer une copie de l’élément de travail**, **développer tout**, **réduire tout** et **créer une tâche utilisateur**.

### <a name="command-placement-decisions"></a>Décisions relatives au positionnement des commandes
 Une fois que vous avez décidé de créer une commande, vous devez déterminer son emplacement approprié et s’il faut créer un raccourci clavier. Suivez ce chemin de décision pour déterminer où placer la commande :

 ![Graphique de décision de positionnement de commandes](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")

 **Chemin de décision pour le positionnement des commandes dans Visual Studio**

### <a name="command-placement-in-menus"></a>Positionnement des commandes dans les menus

#### <a name="main-menu-bar"></a>Barre de menus principale
 La barre de menus principale doit être l’emplacement standard pour les commandes de tous les packages de menu spécifiques au contexte qui contribuent à l’interface utilisateur. La barre de menus principale diffère des autres structures de commande en ce que l’environnement l’utilise pour contrôler les commandes qui sont visibles. Toutes les autres barres de commandes désactivent simplement les commandes qui ne sont pas dans le contexte, qu’elles soient placées dans un menu ou dans une barre d’outils.

 L’environnement définit un ensemble de commandes intégrées à la barre de menus principale qui sont communes à l’ensemble de l’IDE et à plusieurs domaines de tâches. Ces commandes sont toujours visibles, quels que soient les VSPackages chargés dans l’environnement. Bien que les VSPackages puissent étendre cet ensemble de commandes, le jeu de commandes de chaque produit et le positionnement de leurs commandes sont la responsabilité de chaque équipe.

 La structure du menu principal de Visual Studio peut être décomposée dans les catégories de menu suivantes :

##### <a name="core-menus"></a>Menus principaux

- Fichier

- Modifier

- Affichage

- Outils

- Fenêtre

- Aide

##### <a name="project-specific-menus"></a>Menus spécifiques au projet

- Project

- Build

- Débogage

##### <a name="context-specific-menus"></a>Menus spécifiques au contexte

- Équipe

- Données

- Test

- Architecture

- Analyser

##### <a name="document-specific-menus"></a>Menus spécifiques au document

- Format

- Table de charge de travail

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Lorsque vous concevez des menus principaux, respectez les règles suivantes :

- Ne dépassez pas 25 éléments de niveau supérieur dans un contexte donné

- La hauteur des menus ne doit jamais dépasser 600 pixels.

- Évaluez un menu principal dans plusieurs contextes, par exemple dans la référence finale et le profil général.

- Les menus volants sont acceptables.

- Les menus volants doivent contenir au moins trois éléments et pas plus de sept.

- Les menus volants ne doivent atteindre qu’un niveau profond : certains éléments de menu Visual Studio ont des sous-menus en cascade, mais ce modèle n’est pas encouragé.

- N’utilisez pas plus de six séparateurs. Les regroupements doivent respecter l’illustration suivante :

     ![Instructions pour le regroupement du menu principal](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-b_MainMenus")

- Bien qu’il ne soit pas nécessaire d’avoir chaque regroupement dans la figure, l’ajout de regroupements supplémentaires est limité.

- Chaque regroupement doit avoir entre deux et sept éléments de menu.

#### <a name="main-menu-ordering"></a>Classement du menu principal
 Avant d’ajouter un nouvel élément de niveau supérieur, envisagez de placer la commande dans un menu de niveau supérieur existant. Lorsque vous ajoutez un nouveau menu de niveau supérieur, veillez à le placer à l’emplacement approprié. Décidez si le menu est spécifique au projet, au contexte ou au document. Conservez le nom du menu de niveau supérieur concis et utilisez un seul mot.

 Les menus principaux doivent bookend le reste des commandes. Le fichier, la modification et l’affichage doivent toujours être à gauche, et les outils, la fenêtre et l’aide doivent toujours être à droite.

#### <a name="context-menus"></a>Menu contextuels
 Le placement d’un trop grand nombre de fonctionnalités dans les menus contextuels entraîne une interface difficile à apprendre. Toutes les fonctionnalités principales doivent être disponibles par le biais de la barre de menus principale. Le positionnement des commandes doit être rapproché avec les commandes existantes pour éviter les commandes en double. Pour les menus contextuels, le shell définit les groupes de menus standard qui doivent être inclus selon que le menu contextuel est destiné à la solution, à un nœud de projet ou à un élément de projet.

 Lorsque vous concevez des menus contextuels, respectez les mêmes règles que pour le menu principal et, en outre :

- Ne dépassez pas 25 éléments de menu de niveau supérieur.

- Les menus volants sont acceptables, mais ne doivent pas dépasser un niveau de profondeur. n’utilisez jamais de lanceurs en cascade.

- N’utilisez pas plus de six séparateurs.

### <a name="command-placement-in-toolbars"></a>Positionnement des commandes dans les barres d’outils

#### <a name="general-toolbars"></a>Barres d’outils générales
 Lors de la conception et de l’Organisation des barres d’outils, suivez ces normes :

- N’utilisez pas plus d’un verbe par bouton. Un bouton = une action.

- Utilisez le texte en regard de l’icône uniquement s’il doit être renforcé avec l’étiquette.

- Utilisez une zone de liste modifiable exclusivement pour les propriétés qui seront basculées plusieurs fois dans une session. Sinon, exposez la propriété ailleurs.

- La largeur d’une zone de liste déroulante doit être égale à la largeur de l’élément le plus long dans la zone + 30%. Par exemple, si l’élément le plus long est 200 pixels, la zone de liste déroulante doit avoir une largeur de 260 pixels.

- Limitez l’utilisation des séparateurs. L’utilisation d’un séparateur en regard d’une liste déroulante est un anti-modèle, car la forme de la liste déroulante elle-même agit comme un séparateur visuel.

- Les groupes d’icônes doivent contenir entre trois et six icônes.

- Si les qualificateurs génèrent plusieurs commandes utiles, utilisez un bouton partagé qui stocke le dernier paramètre :

     ![Boutons Fractionner dans Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")

     **Exemple de bouton partagé. Les six commandes à gauche peuvent être insérées dans un seul bouton.**

#### <a name="product-specific-toolbars"></a>Barres d’outils spécifiques à un produit
 Chaque produit peut fournir une barre d’outils par défaut qui contient les commandes les plus fréquemment utilisées et importantes, et la barre d’outils par défaut de chaque produit doit apparaître la première fois que Visual Studio démarre après l’installation du produit.

 Les produits doivent également tirer parti des groupes de commandes partagés et des menus fournis par l’IDE. Chaque groupe de commandes partagé est placé dans un menu partagé destiné à organiser les commandes associées de manière significative pour l’utilisateur. Il est important de tirer parti de cette structure de commandes partagée afin de réduire la complexité.

#### <a name="global-toolbars"></a>Barres d’outils globales
 Les barres d’outils globales sont nécessaires pour tenir sur une seule ligne immédiatement. Lorsque vous créez une nouvelle barre d’outils globale, suivez les instructions pour ce type de barre d’outils.

 **Instructions générales de la barre d’outils :**

- Chaque barre d’outils a 24 pixels dans les contrôles communs (pince, dépassement).

- Chaque bouton de barre d’outils est de 22 pixels de largeur, y compris le remplissage. Si vous faites de l’icône un bouton partagé, vous ajoutez 11 pixels de largeur.

- La duplication des commandes entre les barres d’outils est autorisée.

  Les **barres d’outils spécifiques au document** s’affichent lorsqu’un certain type de fichier est actif et disparaissent lorsqu’un autre type de fichier devient actif.

- Les barres d’outils spécifiques au document ne peuvent pas comporter plus de 12 boutons.

- La largeur totale de la barre d’outils ne doit pas dépasser 300 pixels.

- Chaque type de fichier peut avoir soit une barre d’outils incorporée, soit une barre d’outils globale spécifique à un document, mais pas les deux.

  Les **barres d’outils spécifiques au contexte** apparaissent lorsqu’un contexte spécifique est défini et ont tendance à rester actives pendant des périodes prolongées.

- La limite de bouton pour toutes les barres d’outils spécifiques au contexte est 18.

- Si la plupart des utilisateurs n’utilisent pas systématiquement les commandes de cette barre d’outils lorsque le contexte est actif, n’associez pas cette barre d’outils à un contexte.

- Vérifiez que la barre d’outils disparaît en quittant le contexte. Aucune de ces barres d’outils ne doit apparaître au démarrage.

  **Les barres d’outils sans contexte n'** apparaissent jamais automatiquement. Celles-ci s’affichent uniquement lorsque l’utilisateur les active. Conservez la largeur maximale en dessous de 200 pixels.

### <a name="general-organization-and-shell-defined-groups"></a>Groupes généraux définis par l’organisation et l’interpréteur de commandes
 Utilisez les commandes partagées, les groupes de commandes et les menus existants. Si vous devez définir une nouvelle commande, essayez de la placer dans un groupe de commandes partagé existant. Si un nouveau groupe doit être défini, essayez de le placer dans un menu partagé existant à proximité d’un groupe de commandes associé avant de créer un menu de niveau supérieur. Cela réduit la complexité des commandes tout en garantissant un positionnement cohérent des commandes dans l’IDE.

 Le menu **format** partagé, généralement affiché dans le contexte des fenêtres de document de style concepteur, est illustré dans l’image suivante :

 ![Menu Format Visual Studio avec légendes](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")

 **Groupes de menus dans Visual Studio**

### <a name="reducing-and-reusing-commands"></a>Réduction et réutilisation des commandes
 Les commandes sont généralement affichées en fonction du contexte, afin de réduire le nombre de commandes que l’utilisateur voit à un moment donné. Toutefois, vous devez également réutiliser des menus et des groupes de commandes partagés existants pour vous assurer que la structure de la commande reste relativement stable entre les modifications en contexte.

 La réutilisation des commandes partagées et le placement de nouvelles commandes proches des commandes partagées associées réduit la complexité de l’IDE et crée une expérience plus conviviale.

## <a name="naming-commands"></a>Commandes de nom

### <a name="naming-conventions"></a>Conventions d’affectation de noms
 L’attribution d’un nom de commande cohérent est essentielle afin que les utilisateurs puissent Rechercher et exécuter des commandes, en utilisant la ligne de commande ou en liant une liaison à un raccourci clavier. Les noms de commande aident également l’utilisateur à comprendre à quoi sert une commande lorsqu’elle est affichée dans une barre d’outils ou dans un menu contextuel ou en cascade.

#### <a name="when-naming-commands"></a>Lorsque vous nommez des commandes :

- Construisez le texte afin qu’il soit facilement localisable. Pour plus d’informations sur la localisation de texte, consultez [meilleures pratiques](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices)pour la localisation.

- Soyez concis. Les commandes ne doivent pas utiliser plus de trois mots.

- Utiliser la mise en majuscules de la casse : la première lettre de chaque mot doit être en majuscule. Pour plus d’informations sur la mise en forme du texte dans Visual Studio, consultez [style de texte](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

- Tenez compte de l’endroit où la commande sera placée. S’agit-il d’un menu ou d’un menu volant de niveau supérieur ? Par exemple, lors du regroupement des commandes d’alignement dans un lanceur, la commande de niveau supérieur doit être « align » et les commandes de menu volant doivent être « Left », « Right », « Center », « Justify », et ainsi de suite. Il serait redondant de nommer les commandes de menu volant « aligner à gauche » ou « aligner à droite ».

     ![Menu Format Visual Studio](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>Utilisation d’icônes avec des commandes
 Utilisez l’appariement d’icônes avec les commandes. Bien que l’Association d’une image unique à une commande Hastens la capacité de l’utilisateur à identifier cette commande, l’encombrement visuel et l’inefficacité se produisent avec la surutilisation de l’image. Les règles suivantes permettent de décider s’il faut créer une icône de commande.

#### <a name="use-an-icon-with-a-command-only-if"></a>Utilisez une icône avec une commande uniquement si :

- Une icône est associée à la même commande dans un autre produit Microsoft, tel que l’une des applications Microsoft Office.

- La commande est placée dans une barre d’outils par défaut.

- La commande est une commande spécialisée que les utilisateurs sont susceptibles d’ajouter à une barre d’outils à l’aide de la boîte de dialogue **« personnaliser... »** .

## <a name="access-and-shortcut-keys"></a>Touches d’accès et de raccourci

### <a name="overview"></a>Vue d’ensemble
 Il existe deux types d’affectations de touches du clavier :

- Les **touches d’accès** rapide (également appelées accélérateurs) autorisent l’accès au clavier via les menus pour la commande et pour chaque étiquette dans l’interface utilisateur du dialogue. Les clés d’accès sont principalement destinées à l’accessibilité, sont assignées à tous les menus et à la plupart des contrôles de boîte de dialogue, ne sont pas censés être mémorisés, affectent uniquement la fenêtre active et sont localisés.

- Les **touches de raccourci** utilisent principalement des séquences de touches de contrôle (Ctrl) et de fonction (FN). Ils sont plus conçus pour les utilisateurs expérimentés et contribuent à la productivité. Ils sont affectés uniquement aux commandes les plus fréquemment utilisées et permettent un accès rapide tout en contournant le menu principal. Les touches de raccourci sont destinées à être mémorisées et, pour cette raison, doivent être assignées au schéma de profil. Les modèles de touches de raccourci peuvent varier d’un profil à l’autres. Un utilisateur peut personnaliser les touches de raccourci par le biais des **outils > Options > clavier**.

### <a name="assigning-access-keys"></a>Attribution de clés d’accès
 Les clés d’accès se composent de touches Alt + alphanumériques. Assignez une touche d’accès à chaque élément de menu sans exception. Suivez les conventions Windows et communes pour l’attribution de clés d’accès. par exemple, la clé d’accès pour le **fichier > New** doit toujours être **ALT, F, N**.

 N’utilisez pas de lettres de largeur simple, telles que « i » (en majuscules ou en minuscules) ou une « l » minuscule, et évitez d’utiliser des caractères avec des descendants (g, j, p, q et y), car ils sont difficiles à distinguer.

 Évitez d’utiliser des clés dupliquées lorsque cela est possible. Dans les cas où la duplication est inévitable, le système de menus gère les conflits en parcourant toutes les commandes qui utilisent la clé. Par exemple, pour une commande hypothétique « nombre » dans le menu fichier qui duplique la clé d’accès « N », **ALT, f, n** créerait un nouveau fichier, et **ALT, f, n, n** exécuterait la commande « nombre ».

### <a name="assigning-shortcut-keys"></a>Affecter des touches de raccourci
 Évitez d’assigner de nouvelles touches de raccourci, car elles ne sont pas requises pour chaque commande et les taxes du système (et de la mémoire utilisateur) en cas de surutilisation. Les données de l’Programme d’amélioration des services (CEIP) indiquent que les utilisateurs de Visual Studio n’utilisent qu’un petit sous-ensemble des raccourcis intégrés.

 Quand vous définissez des raccourcis, procédez comme suit :

- **Utilisez des séquences de touches de contrôle (Ctrl) et de fonction (FN).**

- **Conserver les raccourcis fréquemment utilisés.** Tenez à jour les raccourcis les plus populaires.

- **Facilitez la saisie des raccourcis de l’éditeur.** Liez des raccourcis faciles à taper aux commandes dont les développeurs ont le plus besoin lors de l’écriture de code. Par exemple, **Edit. InvokeSmartTag** doit avoir une touche de raccourci rapide comme CTRL +/et non ALT + MAJ + F10.

- **Efforcez-vous de disposer de raccourcis cohérents.**

- **Suivez les instructions de Windows pour déterminer les touches de modification à employer.** Utilisez les combinaisons de touches Ctrl pour les commandes qui ont des effets à grande échelle, telles que les commandes qui s’appliquent à un document entier. Utilisez les combinaisons de touches Maj pour les commandes qui étendent ou complètent les actions de la touche de raccourci standard. N’utilisez pas de combinaisons CTRL + ALT.

- **Supprimer les raccourcis superflus.** Si vous disposez d’une fonctionnalité héritée, envisagez de supprimer les raccourcis utilisés avec une infréquence extrême (moins de 10 fois par rapport aux données CEIP) ou une infréquence modérée (moins de 100 fois à partir des données CEIP) si une clé d’accès fournit un accès rapide à la même commande. Par exemple : Alt, H, C ouvre aide/Sommaire.

  Il n’existe pas de moyen simple de vérifier la disponibilité du raccourci. Si vous souhaitez ajouter un raccourci, procédez comme suit :

1. Vérifiez la liste des [raccourcis de Visual Studio 2013](http://visualstudioshortcuts.com/2013/) pour déterminer s’il existe des commandes similaires pour regrouper les vôtres.

2. Accédez à **outils > Options > environnement > clavier** et testez votre raccourci. Vérifiez chaque schéma de configuration du clavier listé sous « appliquer le schéma de configuration du clavier supplémentaire suivant ». Vérifiez les profils généraux, C#, VB et C++, car ils partagent des raccourcis uniques. Votre raccourci est disponible s’il n’est mappé dans aucun de ces emplacements.
