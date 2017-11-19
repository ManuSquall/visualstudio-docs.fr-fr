---
title: Menus et commandes de Visual Studio | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 408a496b78defbca928420f39ebdf9e9de718019
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="menus-and-commands-for-visual-studio"></a>Menus et commandes de Visual Studio
## <a name="command-usage"></a>Utilisation de la commande  
  
### <a name="overview"></a>Vue d'ensemble  
 Contrairement à Microsoft Office, qui est une suite qui comprend de nombreux produits distincts, Visual Studio contient de nombreux produits que chaque contribue leurs jeux de commandes à l’IDE de Visual Studio global. L’IDE gère la complexité des milliers de commandes en filtrant les fonctionnalités disponibles pour l’utilisateur en fonction du contexte.  
  
 Quand le contexte de l’utilisateur change - tels que le basculement à partir d’une fenêtre de conception pour un fenêtre d’édition de code, fonctionnalités sans relation avec le nouveau contexte disparaît. En même temps, nouvelle fonctionnalité est proposée ainsi que des informations dynamiques associées, telles que les options de boîte à outils et de propriétés. L’utilisateur ne doit remarquer la permutation du jeu de commandes disponibles. Si l’utilisateur soit gênés par les commandes apparaître ou disparaître, puis la conception de l’interface utilisateur a besoin d’ajustement. Le contexte de l’utilisateur actuel est toujours indiqué dans une ou plusieurs façons, comme dans la barre de titre IDE, la fenêtre Propriétés ou la boîte de dialogue Pages de propriétés.  
  
 Barres de commandes de permettant une grande flexibilité dans l’interface utilisateur. La seule commande structures inhérente à l’environnement sont le menu principal et la barre de commandes principal, ce qui peut être personnalisée et même masquée de Visual Studio. Autres barres apparaissent et disparaissent en fonction de l’état de l’application. Les éditeurs de document et les fenêtres Outil peuvent également contenir des barres d’outils incorporées dans leurs bords de la fenêtre.  
  
#### <a name="basic-guidelines"></a>Recommandations de base  
  
##### <a name="use-existing-shared-commands-command-groups-and-menus-whenever-possible"></a>Utilisez les commandes partagées existantes, les groupes de commandes et les menus autant que possible.  
 Étant donné que les commandes sont généralement indiquées en contexte, utilisation de menus partagées existantes et de groupes de commandes permet de s’assurer que la structure de la commande reste relativement stable entre les changements de contexte. Réutilisation de commandes partagés et placer les nouvelles commandes proche des commandes partagées associées également réduit la complexité de l’IDE et crée une expérience plus conviviale. Si une nouvelle commande doit être définie, essayez de le placer dans un groupe existant de la commande partagé. Si un nouveau groupe doit être défini, placez-le dans un menu existant partagé proche d’un groupe de commandes associées avant de créer un nouveau menu de niveau supérieur.  
  
##### <a name="do-not-create-icons-for-every-command"></a>Ne créez pas d’icônes pour chaque commande.  
 Réfléchissez bien avant de créer une icône de commande. Icônes doivent être créés uniquement pour les commandes qui :  
  
-   affiche une barre d’outils par défaut.  
  
-   sont susceptibles d’être ajoutées par les utilisateurs à une barre d’outils via le **personnaliser...**  boîte de dialogue.  
  
-   ont une icône associée à la même action dans un autre produit Microsoft.  
  
##### <a name="limit-the-addition-of-keyboard-shortcuts"></a>Limiter l’ajout des raccourcis clavier  
 La grande majorité des utilisateurs utilisent un tout petit nombre de tous les raccourcis clavier disponibles. En cas de doute, ne liez pas votre fonctionnalité à un raccourci clavier. Travail avec votre utilisateur expérience équipe avant d’ajouter de nouveaux raccourcis.  
  
##### <a name="give-commands-a-default-menu-placement"></a>Donner un placement de menu par défaut des commandes.  
 N’oubliez pas que vos commandes seront personnalisées par d’autres utilisateurs et leur conception en conséquence. Il n’existe pas comme une commande masquée. Toutes les commandes de Visual Studio s’affichent dans le **Outils > Personnaliser** boîte de dialogue, la fenêtre de commande, saisie semi-automatique, la **Outils > Options > clavier** boîte de dialogue et l’environnement DTE (Development Tools). Veillez à donner à vos commandes un nom et une info-bulle dans votre fichier .ctc afin que les utilisateurs puissent les trouver facilement.  
  
##### <a name="do-not-duplicate-shared-commands-on-an-embedded-toolbar"></a>Ne dupliquent pas des commandes partagés sur une barre d’outils incorporée.  
 Il est utile de placer des commandes à proximité de la zone de focus de l’utilisateur. Un pour ce faire consiste à créer une barre d’outils incorporée en haut de votre fenêtre outil ou d’un document éditeur. Les commandes placées sur la barre d’outils doivent être spécifiques à la zone de contenu dans la fenêtre. Ne dupliquent pas des commandes partagées sur ces barres d’outils. Par exemple, ne placez jamais une icône de « Enregistrer » dans une barre d’outils incorporée.  
  
### <a name="content-and-command-visibility"></a>Visibilité de contenu et de commande  
 Commandes existent dans les étendues suivantes : **environnement**, **hiérarchie**, et **Document**. Connaître chaque étendue afin d’avoir confiance dans la sélection élective de la commande.  
  
 Commandes dans le **environnement** étendue établir le contexte principal et sont partagés entre plusieurs contextes. Elles modifient la visibilité ou la disposition des fenêtres Outil et les documents. Parmi les commandes dans l’environnement de portée sont **nouveau projet**, **se connecter au serveur**, **attacher processus**, **couper**,  **Copie**, **coller**, **trouver**, **Options**, **personnaliser**, **nouvelle fenêtre**, et **afficher l’aide**.  
  
 Commandes dans le **hiérarchie** étendue de gérer des hiérarchies dans Visual Studio, notamment **projet**, **équipe**, et **données**. Elles se rapportent à sous-contexte d’un projet - par exemple, **déboguer**, **générer**, **Test**, **Architecture**, ou **analyser** . Parmi les commandes dans la hiérarchie de portée sont **ajouter un nouvel élément**, **nouvelle requête**, **les paramètres de projet**, **ajouter une nouvelle Source de données**, **Lancer l’Assistant Performance**, et **nouveau diagramme**.  
  
 Commandes dans le **Document** act étendue sur le contenu d’un document, tels que le code, de création ou d’une requête d’élément de travail (WIQ). Également, ils agissent sur la vue d’une fenêtre outil ou sont spécifiques à cette fenêtre d’outils. Commandes de portée document également agiront sur les objets de fichier qui sont elles-mêmes hiérarchie spécifiques, telles que **supprimer du projet**. Parmi les commandes dans le document sont étendue **refactoriser > Renommer**, **créer une copie de l’élément de travail**, **développer tout**, **réduire tout**, et **Créer une tâche personnalisée**.  
  
### <a name="command-placement-decisions"></a>Décisions de sélection élective de commande  
 Une fois que vous avez décidé de créer une commande, vous devez déterminer sa position appropriée et s’il faut créer un raccourci clavier. Suivez ce chemin d’accès de l’arbre de décision pour établir l’emplacement de la commande :  
  
 ![Graphique de décision de positionnement de commande](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501-a_CommandPlacement")  
  
 **Chemin d’accès de l’arbre de décision pour la sélection élective de commande dans Visual Studio**  
  
### <a name="command-placement-in-menus"></a>Placement de commande dans les menus  
  
#### <a name="main-menu-bar"></a>Barre de menus principale  
 La barre de menus principale doit être l’emplacement standard pour les commandes de tous les packages de menu contextuel spécifiques qui contribuent à l’interface utilisateur. La barre de menus principale est différente des autres structures de commande l’environnement utilise pour contrôler les commandes qui sont visibles. Toutes les autres barres désactivez simplement les commandes qui sont hors contexte, si elles sont placées dans un menu ou une barre d’outils.  
  
 L’environnement définit un ensemble de commandes intégrées à la barre de menus principale qui sont communes à l’ensemble de l’IDE et plusieurs domaines de la tâche. Ces commandes sont toujours visibles, dont les VSPackages sont chargés dans l’environnement. Bien que les VSPackages peuvent étendre cet ensemble de commandes, la commande à partir de chaque produit et le placement de leurs commandes est la responsabilité de chaque équipe.  
  
 La structure du menu principal Visual Studio peut être répartie dans les catégories de menu suivantes :  
  
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
  
-   Déboguer  
  
##### <a name="context-specific-menus"></a>Menus spécifiques au contexte  
  
-   Équipe  
  
-   Données  
  
-   Tester  
  
-   Architecture  
  
-   Analyze  
  
##### <a name="document-specific-menus"></a>Menus spécifiques au document  
  
-   Format  
  
-   Table  
  
##### <a name="when-designing-main-menus-adhere-to-these-rules"></a>Lorsque vous concevez les menus principaux, respecter les règles :  
  
-   N’est pas supérieure à 25 éléments de niveau supérieur dans un contexte donné  
  
-   Menus ne doivent jamais dépasser 600 pixels en hauteur.  
  
-   Évaluer un menu principal dans plusieurs contextes, tels que dans l’Édition intégrale et le profil général.  
  
-   Menus volants sont acceptables.  
  
-   Menus volants doivent contenir au moins trois éléments et pas plus de sept.  
  
-   Menus volants doivent devenir un seul niveau de profondeur : certains éléments de menu Visual Studio comportent des sous-menus en cascade, mais ce modèle n’est pas recommandé.  
  
-   Utilisez des séparateurs pas plus de six. Regroupements doivent respecter l’illustration suivante :  
  
     ![Recommandations pour le regroupement du menu principal](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501-b_MainMenus")  
  
-   Il n’est pas requis pour que chaque regroupement dans la figure, l’ajout des regroupements supplémentaires est limitée.  
  
-   Chaque regroupement doit disposer de deux à sept éléments de menu.  
  
#### <a name="main-menu-ordering"></a>Commande de menu principal  
 Avant d’ajouter un nouvel élément de niveau supérieur, envisagez de placer la commande dans un menu de niveau supérieur existant. Lorsque vous ajoutez un nouveau menu de niveau supérieur, veillez à placer dans l’emplacement correct. Décider si le menu est spécifique au projet, de contexte ou de document. Conserver le nom de menu de niveau supérieur concis et n'utiliser qu’un seul mot.  
  
 Les menus principaux doivent serre-livres le reste des commandes. Fichier, de modifier et d’affichage doivent toujours à gauche et les outils, la fenêtre, et aide doit toujours être vers la droite.  
  
#### <a name="context-menus"></a>Menus contextuels  
 Placer la fonctionnalité de trop dans les menus contextuels des résultats dans une interface difficile à apprendre. Toutes les fonctionnalités principales doivent être disponible via la barre de menus principale. Emplacement de la commande doit être harmonisée avec les commandes existantes afin d’éviter les commandes en double. Pour les menus contextuels, l’interpréteur de commandes définit les groupes de menus standard qui doivent être inclus selon que le menu contextuel est pour la solution, un nœud de projet ou un élément de projet.  
  
 Lors de la conception des menus contextuels, respecter les mêmes règles que pour le menu principal et en outre :  
  
-   Ne dépassez pas 25 des éléments de menu de niveau supérieur.  
  
-   Menus volants sont acceptables, mais doit pas dépasser un niveau de profondeur ; n’utilisez jamais lanceurs en cascade.  
  
-   Utilisez des séparateurs pas plus de six.  
  
### <a name="command-placement-in-toolbars"></a>Placement de commande dans les barres d’outils  
  
#### <a name="general-toolbars"></a>Barres d’outils générales  
 Lorsque vous concevez et réorganiser les barres d’outils, suivez ces normes :  
  
-   N’utilisez pas plus d’un verbe par bouton. Un seul bouton = une action.  
  
-   Utilisez le texte en même temps que l’icône uniquement si elle doit être complété par une étiquette.  
  
-   Utiliser une zone de liste déroulante exclusivement pour les propriétés qui va passer plusieurs fois dans une session. Dans le cas contraire, exposent la propriété ailleurs.  
  
-   La largeur d’une zone de liste modifiable doit être égal à la largeur de l’élément le plus long dans la zone + 30 %. Par exemple, si l’élément le plus long est 200 pixels, la zone de liste modifiable doit être 260 pixels de large.  
  
-   Limiter l’utilisation de séparateurs. L’utilisation d’un séparateur en regard d’une liste déroulante est un anti-modèle, étant donné que la forme de la liste déroulante lui-même agit comme un séparateur visuel.  
  
-   Groupes de l’icône doivent contenir de trois à six icônes.  
  
-   Si les résultats de qualificateurs dans plusieurs commandes utiles, utilisez un bouton partagé qui stocke le dernier paramètre :  
  
     ![Boutons Fractionner dans Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501-c_SplitButtons")  
  
     **Exemple d’un bouton partagé. Les commandes de gauche six peuvent s’ajuster à la place dans un seul bouton.**  
  
#### <a name="product-specific-toolbars"></a>Barres d’outils spécifiques au produit  
 Chaque produit peut fournir une valeur par défaut barre d’outils qui contient fréquemment utilisés et commandes importantes et barre d’outils de la valeur par défaut de chaque produit doivent apparaître au premier démarrage de Visual Studio après avoir installé le produit.  
  
 Produits doivent aussi tirer parti de groupes de commandes partagées et les menus fournis par l’IDE. Chaque groupe de commandes partagé est placé dans un menu partagé permet d’organiser les commandes associées de manière explicite pour l’utilisateur. Il est important de tirer parti de cette structure de commande partagé afin de réduire la complexité.  
  
#### <a name="global-toolbars"></a>Barres d’outils globales  
 Barres d’outils globales sont requis pour s’ajuster à droite d’une ligne en dehors de la zone. Lorsque vous créez une nouvelle barre d’outils globale, suivez les instructions de ce type de barre d’outils.  
  
 **Instructions générales de barre d’outils :**  
  
-   Chaque barre d’outils a 24 pixels dans les contrôles communs (barre de redimensionnement, dépassement de capacité).  
  
-   Chaque bouton de barre d’outils est 22 pixels de larges, y compris le remplissage. Rendre l’icône d’un bouton partagé ajoute un autre 11 pixels de largeur.  
  
-   Duplication de commandes sur les barres d’outils est autorisée.  
  
 **Barres d’outils spécifiques au document** s’affichent lorsqu’un certain type de fichier est actif et disparaissent après un autre type de fichier devient actif.  
  
-   Barres d’outils spécifiques au document ne peuvent pas comporter plus de 12 boutons.  
  
-   La largeur totale de la barre d’outils ne peut pas dépasser 300 pixels.  
  
-   Chaque type de fichier peut avoir une barre d’outils incorporée ou une barre d’outils globale spécifique au document, mais pas les deux.  
  
 **Barres d’outils contextuelle** s’affichent quand un certain contexte est définie et sont susceptibles de rester actif pendant de longues périodes.  
  
-   La limite de bouton pour toutes les barres d’outils de contextuelle est 18.  
  
-   Si la plupart des utilisateurs ne sont pas effectivement constamment les commandes de la barre d’outils lorsque le contexte est actif, puis ne pas associer cette barre d’outils avec un contexte.  
  
-   Assurez-vous que la barre d’outils disparaît lors de la sortie de contexte. Aucun de ces barres d’outils doit apparaître au démarrage.  
  
 **Barres d’outils sans contexte** n’apparaissent jamais automatiquement. Ils apparaissent uniquement lorsque l’utilisateur les active. Conserver la largeur maximale ci-dessous 200 pixels.  
  
### <a name="general-organization-and-shell-defined-groups"></a>Organisation générale et groupes définis par l’interpréteur de commandes  
 Utilisez les commandes partagées existantes, des groupes de commandes et des menus. Si une nouvelle commande doit être définie, essayez de le placer dans un groupe existant de la commande partagé. Si un nouveau groupe doit être définie, essayez de le placer dans un menu existant partagé proche d’un groupe de commandes associées avant de créer un nouveau menu de niveau supérieur. Cela réduit la complexité de la commande tout en garantissant la sélection élective de la commande cohérent dans l’IDE.  
  
 Le partage **Format** menu, généralement indiqué dans le contexte du Concepteur de style des fenêtres de document, est illustré dans l’image suivante :  
  
 ![Menu Format Visual Studio avec légendes](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501-d_FormatMenu")  
  
 **Groupes de menus dans Visual Studio**  
  
### <a name="reducing-and-reusing-commands"></a>Réduction et réutiliser des commandes  
 Commandes généralement affichées sont basées sur le contexte, afin de réduire le nombre de commandes de que l’utilisateur voit à un moment donné. Toutefois, vous devez également le réutiliser des menus partagés existants et des groupes de commandes pour vous assurer que la structure de la commande reste relativement stable entre les changements de contexte.  
  
 Réutilisation de commandes partagés et placer les nouvelles commandes proche des commandes partagées associées réduit la complexité de l’IDE et crée une expérience plus conviviale.  
  
## <a name="naming-commands"></a>Commandes d’affectation de noms  
  
### <a name="naming-conventions"></a>Conventions d'attribution d'un nom  
 Commande cohérent d’affectation de noms est essentielle pour que les utilisateurs peuvent rechercher et exécuter des commandes, soit à l’aide de la ligne de commande ou la liaison à un raccourci clavier. Noms de commande également aident l’utilisateur à quoi sert d’une commande lorsqu’elle est affichée sur une barre d’outils ou dans un menu en cascade ou le contexte.  
  
#### <a name="when-naming-commands"></a>Lorsque d’affectation de noms des commandes :  
  
-   Construire le texte afin qu’il soit facilement localisable. Pour plus d’informations sur la localisation de texte, consultez [préparation World pour Visual Studio](http://msdn.microsoft.com/en-us/1cc35051-8126-441f-bea9-059245a47b1d).  
  
-   Être concis. Les commandes doivent utiliser pas plus de trois mots.  
  
-   Utiliser la mise en majuscules de la casse du titre : la première lettre de chaque mot doit être en majuscule. Pour plus d’informations sur la mise en forme dans Visual Studio, consultez [style de texte](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
-   Prenez en compte dans lequel la commande sera placée. Il est dans un menu de niveau supérieur ou un menu volant ? Par exemple, lorsque les commandes d’alignement de regroupement dans un menu volant, la commande de niveau supérieur doivent être « Align » et les commandes de menu volant doit être « Gauche » « Droite », « Center », « Justify » et ainsi de suite. Il serait redondant pour nommer les commandes de menu volant « Aligné à gauche » ou « Right Align. »  
  
     ![Menu Format Visual Studio](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502-a_FormatMenu")  
  
### <a name="using-icons-with-commands"></a>À l’aide d’icônes avec des commandes  
 À utiliser avec modération de l’utilisation de l’icône de correspondance avec les commandes. Bien que l’association d’une image unique avec une commande empresse la capacité de l’utilisateur pour identifier cette commande, inefficacité et désordre se produisent avec une utilisation abusive de l’image. Les règles suivantes aident lorsque vous décidez s’il faut créer une icône de commande.  
  
#### <a name="use-an-icon-with-a-command-only-if"></a>Utilisez une icône avec une commande uniquement si :  
  
-   La même commande possède une icône associée dans un autre produit Microsoft visible, tel que celui des applications Microsoft Office.  
  
-   La commande sera placée dans une barre d’outils par défaut.  
  
-   La commande est une commande spécialité que les utilisateurs sont susceptibles d’ajouter à une barre d’outils à l’aide de la **« Personnaliser... »** boîte de dialogue.  
  
## <a name="access-and-shortcut-keys"></a>Clés d’accès et le raccourci  
  
### <a name="overview"></a>Vue d'ensemble  
 Il existe deux types d’affectations du clavier :  
  
-   **Clés d’accès** (également appelé accélérateurs) autoriser l’accès de clavier via les menus de l’exécution des commandes et à chaque contrôle label dans la boîte de dialogue l’interface utilisateur. Touches d’accès rapide sont principalement à des fins d’accessibilité, sont attribués à tous les menus et la plupart des contrôles de boîte de dialogue, ne sont pas destinés à être enregistrés, affectent uniquement la fenêtre active et sont localisés.  
  
-   **Touches de raccourci** principalement utiliser contrôle (Ctrl) et les séquences de touches de fonction (Fn). Ils sont plus conçus pour les utilisateurs expérimentés et aide en matière de productivité. Ils sont assignés uniquement à des commandes les plus fréquemment utilisées et permettent un accès rapide en utilisant le menu principal. Touches de raccourci sont destinés à être enregistrés, et pour cette raison doit être affectée cohérent avec le schéma de profil. Schémas de touches de raccourci peuvent varier à chaque profil. Un utilisateur peut personnaliser les touches de raccourci via **Outils > Options > clavier**.  
  
### <a name="assigning-access-keys"></a>Affectation des touches d’accès rapide  
 Les clés d’accès se composent de touches Alt plus alphanumériques. Affecter une touche d’accès à chaque élément de menu sans exception. Suivez les conventions courantes pour assigner des touches d’accès et Windows. par exemple, la clé d’accès **fichier > nouveau** doit toujours être **Alt, F, N**.  
  
 Évitez d’utiliser des lettres de largeur de pixel unique tel que « i » (en majuscules ou minuscules) ou un caractère minuscule « l » et évitez d’utiliser des caractères descendants (g, j, p, q et y) sont difficiles à distinguer.  
  
 Évitez d’utiliser des clés en double lorsque cela est possible. Dans les cas où la duplication est inévitable, le système de menus gère les conflits en parcourant toutes les commandes qui utilisent la clé. Par exemple, pour un hypothétique de commande dans le menu fichier qui duplique la clé d’accès « N », « Number » **Alt, F, N** créerait un nouveau fichier, et **Alt, F, N, N** serait d’exécuter la commande « Nombre ».  
  
### <a name="assigning-shortcut-keys"></a>Affectation des touches de raccourci  
 Évitez d’attribuer de nouvelles touches de raccourci, car ils ne sont pas requis pour toutes les commandes et de taxe le système (et la mémoire de l’utilisateur) si l’utilisation excessive. Données à partir du programme (amélioration) indiquent que les utilisateurs de Visual Studio utilisent uniquement un petit sous-ensemble des raccourcis intégrés.  
  
 Lorsque vous définissez des raccourcis, suivez ces règles :  
  
-   **Utiliser le contrôle (Ctrl) et les séquences de touches de fonction (Fn).**  
  
-   **Conserver les raccourcis fréquemment utilisées.** Mettre à jour les raccourcis les plus populaires.  
  
-   **Faciliter les raccourcis de l’éditeur au type.** Lier à saisir des raccourcis pour les commandes que les développeurs ont besoin de plus, lors de l’écriture de code. Par exemple, **Edit.InvokeSmartTag** doit disposer d’une touche de raccourci rapide comme Ctrl + / et pas Alt + Maj + F10.  
  
-   **S’efforcent de raccourcis de façon cohérente à thème.**  
  
-   **Suivez les instructions de Windows pour déterminer le modificateur de clés à utiliser.** Utilisez les combinaisons de touches Ctrl pour les commandes qui ont des effets à grande échelle, telles que les commandes qui s’appliquent à un document entier. Utilisez les combinaisons de touche MAJ pour les commandes qui étendre ou de complément les actions de la touche de raccourci standard. N’utilisez pas les combinaisons de touches Ctrl + Alt.  
  
-   **Supprimer les raccourcis superflus.** Si vous disposez d’une fonctionnalité héritée, envisagez de supprimer les raccourcis qui sont utilisés avec la fréquence extrêmes (moins de 10 fois à partir des données CEIP) ou mensuelle modérée (moins de 100 fois à partir des données CEIP) si une clé d’accès fournit un accès rapide à la même commande. Par exemple : Alt, H, C ouvrira/sommaire de l’aide.  
  
 Il n’est pas un moyen simple de vérifier la disponibilité de raccourci. Si vous souhaitez ajouter un raccourci, procédez comme suit :  
  
1.  Vérifiez la liste des [Visual Studio 2013 raccourcis](http://visualstudioshortcuts.com/2013/) pour déterminer s’il existe des commandes similaires à regrouper avec le vôtre.  
  
2.  Accédez à **Outils > Options > environnement > clavier** et tester votre raccourci. Vérifiez que chaque schéma de mappage du clavier répertoriés sous « Appliquer le schéma de mappage du clavier. » Vérification des profils de général, c#, VB et C++, comme ceux partagent des raccourcis uniques. Le raccourci est disponible s’il n’est pas mappé dans un de ces emplacements.