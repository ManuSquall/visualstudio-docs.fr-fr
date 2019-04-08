---
title: Menus et commandes
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b0fa441c6dc56210c11a0007eb2662b3c08910ba
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001381"
---
# <a name="menus-and-commands-for-visual-studio"></a>Menus et commandes de Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="command-usage"></a>Utilisation de la commande

### <a name="overview"></a>Vue d'ensemble
 Contrairement à Microsoft Office, qui est une suite qui comprend de nombreux produits distincts, Visual Studio contient de nombreux produits que chaque contribue leurs jeux de commandes à l’IDE de Visual Studio global. L’IDE gère la complexité de milliers de commandes en filtrant les fonctionnalités disponibles pour l’utilisateur en fonction du contexte.

 Lorsqu’un contexte de l’utilisateur change – tels que le basculement à partir d’une fenêtre de conception à un fenêtre d’édition de code – fonctionnalités non liées à nouveau contexte disparaît. En même temps, nouvelle fonctionnalité est proposée ainsi que des informations dynamiques associées, telles que les options de propriétés et de la boîte à outils. L’utilisateur ne remarquerez pas la permutation du jeu de commandes disponibles. Si l’utilisateur est gênés ou perturbés par les commandes qui apparaissent ou disparaissent, la conception de l’interface utilisateur doit ajustement. Le contexte de l’utilisateur actuel est toujours indiqué dans une ou plusieurs façons, comme dans la barre de titre d’IDE, la fenêtre Propriétés ou la boîte de dialogue Pages de propriétés.

 Barres de commandes de permettant une grande flexibilité dans l’interface utilisateur. La seule commande structures inhérentes à l’environnement sont le menu principal et la barre de commandes principal, ce qui peut être personnalisée et même masquée de Visual Studio. Autres barres de commandes apparaissent et disparaissent selon l’état de l’application. Fenêtres Outil et les éditeurs de document peuvent également contenir des barres d’outils incorporées dans leurs bords de fenêtre.

#### <a name="basic-guidelines"></a>Recommandations de base

##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Utiliser des commandes partagées existantes, les groupes de commandes et les menus autant que possible.
 Dans la mesure où les commandes généralement affichées sont basées sur le contexte, utilisation de menus partagés existants et les groupes de commandes garantit que la structure de la commande reste relativement stable entre les changements dans le contexte. Réutilisation des commandes partagées et de placer de nouvelles commandes proche des commandes partagées associées également réduit la complexité de l’IDE et crée une expérience plus conviviale. Si une nouvelle commande doit être définie, essayez de le placer dans un groupe existant de la commande partagé. Si un nouveau groupe doit être défini, le placer dans un menu partagé existant proche d’un groupe de commandes connexes avant de créer un nouveau menu de niveau supérieur.

##### <a name="do-not-create-icons-for-every-command"></a>Ne créez pas d’icônes pour chaque commande.
 Réfléchissez bien avant de créer une icône de commande. Icônes doivent être créées uniquement pour les commandes qui :

-   s’affichent sur une barre d’outils par défaut.

-   sont susceptibles d’être ajoutées par les utilisateurs à une barre d’outils via le **personnaliser...** boîte de dialogue.

-   avoir une icône associée à la même action dans un autre produit Microsoft.

##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limite de l’ajout de raccourcis clavier
 La grande majorité des utilisateurs utilisent une toute petite partie de tous les raccourcis disponibles. En cas de doute, ne liez pas votre fonctionnalité à un raccourci clavier. Travail avec votre utilisateur rencontrer l’équipe avant d’ajouter de nouveaux raccourcis.

##### <a name="give-commands-a-default-menu-placement"></a>Donner des commandes un placement de menu par défaut.
 N’oubliez pas que vos commandes seront personnalisées par d’autres utilisateurs et les concevoir en conséquence. Il n’existe pas comme une commande masquée. Toutes les commandes de Visual Studio s’affichent dans le **Outils > Personnaliser** boîte de dialogue, la fenêtre de commande, saisie semi-automatique, la **Outils > Options > clavier** boîte de dialogue et l’environnement DTE (Development Tools). Veillez à donner à vos commandes un nom et une info-bulle dans votre fichier .ctc afin que les utilisateurs de les trouver facilement.

##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Ne dupliquent pas des commandes partagées dans une barre d’outils incorporée.
 Il est inutile de placer des commandes à proximité de la zone de focus de l’utilisateur. Un pour ce faire consiste à créer une barre d’outils incorporée en haut de votre fenêtre outil ou d’un document éditeur. Les commandes placées dans la barre d’outils doivent être spécifiques à la zone de contenu au sein de la fenêtre. Ne dupliquent pas des commandes partagées sur ces barres d’outils. Par exemple, ne placez jamais une icône de « Enregistrer » au sein d’une barre d’outils incorporée.

### <a name="content-and-command-visibility"></a>Visibilité de contenu et de commande
 Commandes existent dans les étendues suivantes : **Environnement**, **hiérarchie**, et **Document**. Connaître chaque étendue afin d’avoir confiance dans l’emplacement de commande.

 Commandes dans le **environnement** étendue établir le contexte principal et sont partagées entre plusieurs contextes. Modifient la visibilité ou la disposition des documents et des fenêtres Outil. Parmi les commandes dans l’environnement de portée sont **nouveau projet**, **se connecter au serveur**, **attacher processus**, **couper**,  **Copie**, **coller**, **trouver**, **Options**, **personnaliser**, **nouvelle fenêtre**, et **afficher l’aide**.

 Commandes dans le **hiérarchie** étendue gérer les hiérarchies dans Visual Studio, notamment **projet**, **équipe**, et **données**. Elles se rapportent à sous-contexte d’un projet – par exemple, **déboguer**, **Build**, **Test**, **Architecture**, ou **analyser** . Parmi les commandes dans la hiérarchie de portée sont **ajouter un nouvel élément**, **nouvelle requête**, **paramètres du projet**, **ajouter une nouvelle Source de données**, **Lancer l’Assistant Performance**, et **nouveau diagramme**.

 Commandes dans le **Document** act étendue sur le contenu d’un document, telles que code, de conception ou d’une requête d’élément de travail (WIQ). Ils également agissent sur la vue d’une fenêtre outil ou ne sont pas spécifiques à cette fenêtre outil. Commandes d’étendue de document également agiront sur les objets de fichier qui sont eux-mêmes hiérarchie spécifiques, tels que **supprimer du projet**. Parmi les commandes dans le document sont étendue **refactoriser > Renommer**, **créer une copie de l’élément de travail**, **développer tout**, **réduire tout**, et **Créer une tâche personnalisée**.

### <a name="command-placement-decisions"></a>Décisions de placement de commande
 Une fois que vous avez décidé de créer une commande, vous devrez déterminer son positionnement appropriée et s’il faut créer un raccourci clavier. Suivez ce chemin d’accès de décision pour établir où placer la commande :

 ![Graphique de décision de positionnement de commande](../../extensibility/ux-guidelines/media/0501-a-commandplacement.png "0501-a_CommandPlacement")

 **Chemin d’accès de décision pour la sélection élective de commande dans Visual Studio**

### <a name="command-placement-in-menus"></a>Placement de commande dans les menus

#### <a name="main-menu-bar"></a>Barre de menus principale
 La barre de menus principale doit être l’emplacement standard pour les commandes de tous les packages de menu contextuel spécifiques qui contribuent à l’interface utilisateur. La barre de menus principale diffère d’autres structures de commande car l’environnement l’utilise pour contrôler les commandes qui sont visibles. Toutes les autres barres de commandes désactiver simplement les commandes qui sont hors contexte, si elles sont placées dans un menu ou une barre d’outils.

 L’environnement définit un ensemble de commandes intégrées à la barre de menus principale qui sont communes à l’ensemble de l’IDE et plusieurs domaines de la tâche. Ces commandes sont toujours visibles quel que soit dont les VSPackages sont chargés dans l’environnement. Bien que les VSPackages peuvent étendre cet ensemble de commandes, le jeu de commandes depuis chaque produit et le positionnement des commandes est la responsabilité de chaque équipe.

 La structure du menu principal de Visual Studio peut être divisée selon les catégories de menu suivantes :

##### <a name="core-menus"></a>Menus principaux

-   Fichier

-   Modifier

-   Vue

-   Outils

-   Fenêtre

-   Help

##### <a name="project-specific-menus"></a>Menus spécifiques au projet

-   Projet

-   Build

-   Débogage

##### <a name="context-specific-menus"></a>Menus spécifiques au contexte

-   Équipe

-   Données

-   Tester

-   Architecture

-   Analyze

##### <a name="document-specific-menus"></a>Menus spécifiques au document

-   Format

-   Table

##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Lorsque vous concevez des menus principaux, respecter ces règles :

-   Ne dépassez pas 25 éléments de niveau supérieur dans un contexte donné

-   Menus ne doivent jamais dépasser 600 pixels en hauteur.

-   Évaluer un menu principal dans plusieurs contextes, comme dans l’Édition intégrale et le profil général.

-   Menus volants sont acceptables.

-   Menus volants doivent contenir au moins trois éléments et pas plus de sept.

-   Menus volants doivent aller qu’un seul niveau de profondeur : certains éléments de menu de Visual Studio comportent des sous-menus en cascade, mais ce modèle n’est pas recommandée.

-   Utilisez des séparateurs pas plus de six. Regroupements doivent respecter l’illustration suivante :

     ![Instructions pour le regroupement du menu principal](../../extensibility/ux-guidelines/media/0501-b-mainmenus.png "0501-b_MainMenus")

-   Alors qu’il n’est pas nécessaire pour que chaque regroupement dans la figure, l’ajout de regroupements supplémentaires est limité.

-   Chaque regroupement doit avoir de deux à sept éléments de menu.

#### <a name="main-menu-ordering"></a>Commande de menu principal
 Avant d’ajouter un nouvel élément de niveau supérieur, envisagez de placer la commande dans un menu de niveau supérieur existant. Lorsque vous ajoutez un nouveau menu de niveau supérieur, veillez à placer dans l’emplacement approprié. Décider si le menu est spécifique au projet, de contexte ou de document. Conservez le nom de menu de niveau supérieur concis et n'utiliser qu’un seul mot.

 Les menus core doivent serre-livres le reste des commandes. Fichier, de modification et d’affichage doivent toujours être vers la gauche et les outils, fenêtre, et aide doit toujours être vers la droite.

#### <a name="context-menus"></a>Menus contextuels
 Placer la fonctionnalité de trop dans les menus contextuels des résultats dans une interface difficile à maîtriser. Toutes les fonctionnalités principales doivent être disponible via la barre de menus principale. Emplacement de la commande doit être harmonisée avec les commandes existantes afin d’éviter les commandes en double. Pour les menus contextuels, l’interpréteur de commandes définit les groupes de menus standard qui doivent être incluses selon que le menu contextuel est pour la solution, un nœud de projet ou un élément de projet.

 Lorsque vous concevez des menus contextuels, respecter les mêmes règles que pour le menu principal et en outre :

-   Ne dépassez pas 25 des éléments de menu de niveau supérieur.

-   Menus volants sont acceptables, mais doit pas dépasser un niveau de profondeur – n’utilisez jamais de menus volants en cascade.

-   Utilisez des séparateurs pas plus de six.

### <a name="command-placement-in-toolbars"></a>Placement de commande dans les barres d’outils

#### <a name="general-toolbars"></a>Barres d’outils généraux
 Lorsque vous concevez et organisation des barres d’outils, suivez ces normes :

-   N’utilisez pas plusieurs verbes par un bouton. Un bouton = une seule action.

-   Utilisez le texte en même temps que l’icône uniquement si elle doit être complété avec l’étiquette.

-   Utiliser une zone de liste déroulante exclusivement pour les propriétés qui changent plusieurs fois dans une session. Exposer dans le cas contraire, la propriété ailleurs.

-   La largeur d’une zone de liste déroulante doit être égal à la largeur de l’élément le plus long dans la zone + 30 %. Par exemple, si l’élément le plus long est 200 pixels, la zone de liste déroulante doit être 260 pixels de large.

-   Limitez l’utilisation de séparateurs. L’utilisation d’un séparateur en regard d’une liste déroulante est un anti-modèle, étant donné que la forme de la liste déroulante lui-même agit comme un séparateur visuel.

-   Groupes de l’icône doivent contenir de trois à six icônes.

-   Si le résultat de qualificateurs dans plusieurs commandes utiles, utiliser un bouton partagé qui stocke le dernier paramètre :

     ![Boutons Fractionner dans Visual Studio](../../extensibility/ux-guidelines/media/0501-c-splitbuttons.png "0501-c_SplitButtons")

     **Exemple d’un bouton partagé. Les six commandes sur la gauche au lieu de cela tiennent dans un seul bouton.**

#### <a name="product-specific-toolbars"></a>Barres d’outils spécifiques au produit
 Chaque produit peut fournir une valeur par défaut barre d’outils qui contient fréquemment utilisés et commandes importantes et barre d’outils de la valeur par défaut de chaque produit doivent apparaître du premier démarrage de Visual Studio une fois que le produit est installé.

 Produits doivent également tirer parti des groupes de commandes partagées et des menus fournis par l’IDE. Chaque groupe de commandes partagé est placé dans un menu partagé permet d’organiser les commandes associées de manière explicite pour l’utilisateur. Il est important de tirer parti de cette structure de commande partagé afin de réduire la complexité.

#### <a name="global-toolbars"></a>Barres d’outils globales
 Barres d’outils globales sont nécessaires pour tenir sur une ligne emploi. Lorsque vous créez une nouvelle barre d’outils globale, suivez les instructions pour ce type de barre d’outils.

 **Instructions générales de barre d’outils :**

- Chaque barre d’outils a 24 pixels dans les contrôles communs (barre de redimensionnement, un dépassement de capacité).

- Chaque bouton de barre d’outils est de 22 pixels de larges, y compris le remplissage. Rendre l’icône d’un bouton partagé ajoute un autre 11 pixels de largeur.

- Duplication des commandes entre les barres d’outils est autorisée.

  **Barres d’outils spécifiques au document** s’affichent quand un certain type de fichier est actif et disparaissent quand un autre type de fichier devient actif.

- Barres d’outils spécifiques au document ne peuvent pas avoir plus de 12 boutons.

- La largeur totale de la barre d’outils ne doit pas dépasse 300 pixels.

- Chaque type de fichier peut avoir une barre d’outils incorporée ou une barre d’outils globale spécifique au document, mais pas les deux.

  **Barres d’outils contextuelle** apparaissent quand un certain contexte est définie et ont tendance à rester actives pendant des périodes prolongées.

- La limite de bouton pour toutes les barres d’outils contextuelle est 18.

- Si la plupart des utilisateurs ne sont pas systématiquement employez des commandes de la barre d’outils lorsque le contexte est actif, puis ne pas associer cette barre d’outils avec un contexte.

- Assurez-vous que la barre d’outils disparaît lors de la sortie de contexte. Aucune de ces barres d’outils doit apparaître au démarrage.

  **Barres d’outils sans contexte** n’apparaissent jamais automatiquement. Ceux-ci montrent uniquement lorsque l’utilisateur les active. Conserver la largeur maximale ci-dessous 200 pixels.

### <a name="general-organization-and-shell-defined-groups"></a>Organisation générale et des groupes définis par l’interpréteur de commandes
 Utiliser des commandes partagées existantes, les groupes de commandes et les menus. Si une nouvelle commande doit être définie, essayez de le placer dans un groupe existant de la commande partagé. Si un nouveau groupe doit être définie, essayez de le placer dans un menu partagé existant proche d’un groupe de commandes connexes avant de créer un nouveau menu de niveau supérieur. Cela réduit la complexité de la commande tout en garantissant le placement de commande cohérente dans l’IDE.

 Le partagé **Format** menu, généralement affiché dans le contexte du Concepteur de style des fenêtres de document, est illustré dans l’image suivante :

 ![Menu Format Visual Studio avec légendes](../../extensibility/ux-guidelines/media/0501-d-formatmenu.png "0501-d_FormatMenu")

 **Groupes de menus dans Visual Studio**

### <a name="reducing-and-reusing-commands"></a>Réduction et la réutilisation des commandes
 Commandes généralement affichées sont basées sur le contexte, afin de réduire le nombre de commandes de que l’utilisateur voit à un moment donné. Toutefois, vous devez également réutiliser des menus partagés existants et les groupes de commandes pour vous assurer que la structure de la commande reste relativement stable entre les changements de contexte.

 Réutilisation des commandes partagées et placer les nouvelles commandes proche des commandes partagées associées réduit la complexité de l’IDE et crée une expérience plus conviviale.

## <a name="naming-commands"></a>Commandes d’affectation de noms

### <a name="naming-conventions"></a>Conventions d'attribution d'un nom
 Il est essentiel de commande cohérent d’affectation de noms afin que les utilisateurs peuvent rechercher et exécuter des commandes, soit à l’aide de la ligne de commande ou la liaison à un raccourci clavier. Noms de commande également aider l’utilisateur quel but une commande sert lorsqu’elle est affichée sur une barre d’outils ou dans un menu en cascade ou de contexte.

#### <a name="when-naming-commands"></a>Lorsque d’affectation de noms commandes :

-   Construire le texte afin qu’il soit facilement localisable. Pour plus d’informations sur la localisation de texte, consultez [meilleures pratiques de localisation](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps#localization-best-practices).

-   Être concis. Les commandes doivent utiliser pas plus de trois mots.

-   Utiliser la mise en majuscules des mots en majuscule : la première lettre de chaque mot doit être en majuscules. Pour plus d’informations sur la mise en forme dans Visual Studio, consultez [style de texte](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

-   Prenez en compte dans lequel la commande sera placée. Il est dans un menu de niveau supérieur ou un menu volant ? Par exemple, lorsque les commandes d’alignement de regroupement dans un menu volant, la commande de niveau supérieur doivent être « Alignement » et les commandes de menu volant doit être « Gauche » « Droite », « Center », « Justify » et ainsi de suite. Il serait redondant pour nommer les commandes de menu volant « Aligner à gauche » ou « Right Align. »

     ![Menu Format Visual Studio](../../extensibility/ux-guidelines/media/0502-a-formatmenu.png "0502-a_FormatMenu")

### <a name="using-icons-with-commands"></a>À l’aide des icônes avec les commandes
 Être proactif dans l’utilisation de l’icône de couplage avec les commandes. Bien que l’association d’une image unique avec une commande accélère grandement la capacité d’utilisateur à identifier cette commande, inefficacité et encombrement visuel se produisent avec une utilisation abusive de l’image. Les règles suivantes vous aident lorsque vous décidez s’il faut créer une icône de commande.

#### <a name="use-an-icon-with-a-command-only-if"></a>Utiliser une icône avec un commande que si :

-   La même commande possède une icône associée dans un autre produit Microsoft principales, tel que celui des applications Microsoft Office.

-   La commande sera placée dans une barre d’outils par défaut.

-   La commande est une commande de spécialisation que les utilisateurs sont susceptibles d’ajouter à une barre d’outils à l’aide de la **« Personnaliser... »** boîte de dialogue.

## <a name="access-and-shortcut-keys"></a>Clés d’accès et de raccourci

### <a name="overview"></a>Vue d'ensemble
 Il existe deux types d’affectations du clavier :

-   **Clés d’accès** (également appelé accélérateurs) autorisent l’accès de clavier via les menus pour la commande et à chaque contrôle label dans la boîte de dialogue interface utilisateur. Clés d’accès sont principalement à des fins d’accessibilité sont attribués à tous les menus et la plupart des contrôles de boîte de dialogue, ne sont pas destinés à être retenu, affectent uniquement la fenêtre active et sont localisés.

-   **Touches de raccourci** principalement utiliser contrôle (Ctrl) et les séquences de touches de fonction (Fn). Elles sont plus conçues pour les utilisateurs expérimentés et aide la productivité. Ils sont assignés uniquement à des commandes les plus fréquemment utilisées et autoriser l’accès rapide tout en ignorant le menu principal. Touches de raccourci sont destinées à être retenu, et pour cette raison doit être affectée cohérent avec le schéma de profil. Schémas de touches de raccourci peuvent varier à partir d’un profil à un profil. Un utilisateur peut personnaliser les touches de raccourci via **Outils > Options > clavier**.

### <a name="assigning-access-keys"></a>Affectation des clés d’accès
 Clés d’accès sont constitués de touches Alt plus d’alphanumériques. Affecter une touche d’accès à chaque élément de menu sans exception. Suivez Windows et des conventions communes pour l’affectation des clés d’accès. par exemple, la clé d’accès **fichier > nouveau** doit toujours être **Alt, F, N**.

 N’utilisent pas des lettres de largeur de pixel unique tel que « i » (en majuscule ou minuscule) ou une minuscule « l » et évitez d’utiliser des caractères descendants (g, j, p, q et y) car ceux-ci sont difficiles à distinguer.

 Évitez d’utiliser des clés en double lorsque cela est possible. Dans les cas où une duplication est inévitable, le système de menu gère les conflits en parcourant toutes les commandes qui utilisent la clé. Par exemple, pour un hypothétique de commande dans le menu fichier qui duplique la clé d’accès « N », « Number » **Alt, F, N** créerait un nouveau fichier, et **Alt, F, N, N** exécuterait la commande « Nombre ».

### <a name="assigning-shortcut-keys"></a>Affectation des touches de raccourci
 Évitez d’attribuer de nouvelles touches de raccourci, car ils ne sont pas requises pour chaque commande et de taxe le système (et la mémoire de l’utilisateur) si l’utilisation excessive. Les données à partir du programme (amélioration) indiquent que les utilisateurs de Visual Studio utilisent uniquement un petit sous-ensemble des raccourcis intégrés.

 Lorsque vous définissez des raccourcis, suivez ces règles :

- **Utiliser le contrôle (Ctrl) et les séquences de touches de fonction (Fn).**

- **Conserver les raccourcis fréquemment utilisées.** Conserver les raccourcis populaires.

- **Faciliter les raccourcis de l’éditeur au type.** Lier les raccourcis facile vers un type aux commandes que les développeurs doivent la plupart lors de l’écriture de code. Par exemple, **Edit.InvokeSmartTag** doit avoir une touche de raccourci rapide comme Ctrl + / et pas Alt + Maj + F10.

- **S’efforcent de raccourcis de manière cohérente à thème.**

- **Suivez les instructions de Windows pour déterminer quel modificateur touches à employer.** Utilisez les combinaisons de touches Ctrl pour les commandes qui ont des effets à grande échelle, telles que les commandes qui s’appliquent à un document entier. Utiliser des combinaisons de touche MAJ enfoncée pour les commandes qui étendent ou complément les actions de la touche de raccourci standard. N’utilisez pas les combinaisons de touches Ctrl + Alt enfoncées.

- **Supprimer les raccourcis superflues.** Si vous avez une fonctionnalité héritée, envisagez de supprimer les raccourcis qui sont utilisées avec extrême mensuelle (moins de 10 fois à partir des données CEIP) ou mensuelle modéré (moins de 100 fois à partir des données CEIP), si une clé d’accès fournit un accès rapide à la même commande. Exemple : ALT, H, C ouvrira/sommaire de l’aide.

  Il n’est pas un moyen simple de vérifier la disponibilité de raccourci. Si vous souhaitez ajouter un raccourci, procédez comme suit :

1.  Vérifiez la liste des [raccourcis de Visual Studio 2013](http://visualstudioshortcuts.com/2013/) pour déterminer s’il existe des commandes similaires aux vôtres avec groupe.

2.  Accédez à **Outils > Options > environnement > clavier** et tester votre raccourci. Vérifiez que chaque schéma de configuration du clavier est répertorié sous « Appliquer le schéma de mappage de clavier supplémentaires suivantes. » Vérification des profils général, C#, VB et C++, comme ceux partagent les raccourcis uniques. Le raccourci est disponible s’il n’est pas mappé dans un de ces emplacements.
