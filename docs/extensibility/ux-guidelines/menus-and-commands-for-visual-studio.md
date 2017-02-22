---
title: "Menus et commandes de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a1ed675-2bd1-4603-ba3a-f40dfb5cfb69
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# Menus et commandes de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

## Utilisation de la commande  
  
### Vue d'ensemble  
 Contrairement à Microsoft Office, qui est une suite qui comprend de nombreux produits distincts, Visual Studio contient de nombreux produits que chaque contribue leurs jeux de commandes à l'IDE de Visual Studio global. L'IDE gère la complexité des milliers de commandes en filtrant les fonctionnalités disponibles pour l'utilisateur selon le contexte.  
  
 Un contexte de l'utilisateur change, tels que le basculement d'une fenêtre de conception à un fenêtre d'édition de code : fonctionnalité non liés à nouveau contexte disparaît. En même temps, nouvelle fonctionnalité est proposée avec des informations dynamiques associées, telles que les options de propriétés et de la boîte à outils. L'utilisateur ne doit remarquer la permutation de l'ensemble des commandes disponibles. Si l'utilisateur est distrait ou perturbés par les commandes qui apparaissent ou disparaissent, la conception de l'interface utilisateur doit ajustement. Le contexte de l'utilisateur actuel est toujours indiqué dans une ou plusieurs façons, comme dans la barre de titre IDE, la fenêtre Propriétés ou la boîte de dialogue Pages de propriétés.  
  
 Barres de commandes de permettant une grande flexibilité dans l'interface utilisateur. La seule commande structures inhérentes à l'environnement sont le menu principal et la barre de commandes principal, qui peut être personnalisée et même masquée de Visual Studio. Autres barres apparaissent et disparaissent en fonction de l'état de l'application. Les fenêtres Outil et les éditeurs de document peuvent également contenir des barres d'outils incorporées dans leurs bords de la fenêtre.  
  
#### Instructions de base  
  
##### Utilisez les commandes partagés existants, les groupes de commandes et menus autant que possible.  
 Étant donné que les commandes sont généralement indiquées en fonction du contexte, utilisation de menus partagés existants et groupes de commande garantit que la structure de la commande reste relativement stable entre les changements de contexte. Réutilisation de commandes partagés et d'y placer des nouvelles commandes proche des commandes partagées associées également réduit la complexité de l'IDE et crée une expérience plus conviviale. Si une nouvelle commande doit être définie, essayez de le placer dans un groupe de commandes partagé existant. Si un nouveau groupe doit être définie, placez\-le dans un menu partagé existant proche d'un groupe de commandes connexes avant de créer un nouveau menu de niveau supérieur.  
  
##### Ne créez pas d'icônes pour chaque commande.  
 Réfléchissez bien avant de créer une icône de commande. Icônes doivent être créés uniquement pour les commandes qui :  
  
-   affiche une barre d'outils par défaut.  
  
-   sont susceptibles d'être ajoutés par les utilisateurs à une barre d'outils via le **Personnaliser...** boîte de dialogue.  
  
-   avoir une icône associée à la même action dans un autre produit Microsoft.  
  
##### Limiter l'ajout de raccourcis clavier  
 La grande majorité des utilisateurs utilisent une petite fraction de tous les raccourcis disponibles. En cas de doute, ne liez pas votre fonctionnalité à un raccourci clavier. Travail avec l'utilisateur de votre expérience équipe avant d'ajouter de nouveaux raccourcis.  
  
##### Donner des commandes un placement de menu par défaut.  
 N'oubliez pas que vos commandes seront personnalisées par d'autres utilisateurs et de les créer en conséquence. Il n'existe pas comme une commande masquée. Toutes les commandes de Visual Studio s'affichent dans le **Outils \> Personnaliser** boîte de dialogue, la fenêtre de commande, saisie semi\-automatique, le **Outils \> Options \> clavier** boîte de dialogue et l'environnement DTE \(Development Tools\). Veillez à donner à vos commandes un nom et une info\-bulle dans votre fichier .ctc afin que les utilisateurs puissent les trouver facilement.  
  
##### Ne pas copier les commandes partagés sur une barre d'outils incorporée.  
 Il est utile de placer des commandes à proximité de la zone d'intérêt de l'utilisateur. Pour ce faire consiste à créer une barre d'outils incorporée en haut de votre fenêtre outil ou le document éditeur. Les commandes placées sur la barre d'outils doivent être spécifiques à la zone de contenu dans la fenêtre. Ne pas copier les commandes partagés sur ces barres d'outils. Par exemple, ne placez jamais une icône « Enregistrer » au sein d'une barre d'outils incorporée.  
  
### Visibilité de contenu et de commandes  
 Commandes existent dans les étendues suivantes : **environnement**, **hiérarchie**, et **Document**. Connaître chaque étendue afin d'avoir confiance dans l'emplacement de commande.  
  
 Commandes dans le **environnement** étendue établir le contexte principal et sont partagées entre plusieurs contextes. Elles modifient la visibilité ou la disposition des documents et des fenêtres Outil. Parmi les commandes dans l'environnement de portée sont **Nouveau projet**, **se connecter au serveur**, **attacher un processus**, **Couper**, **copie**, **Coller**, **trouver**, **Options**, **Personnaliser**, **nouvelle fenêtre**, et **Afficher l'aide**.  
  
 Commandes dans le **hiérarchie** étendue de gérer des hiérarchies dans Visual Studio, y compris **projet**, **équipe**, et **données**. Ils portent sous\-contexte d'un projet, par exemple, **Debug**, **Build**, **Test**, **Architecture**, ou **analyser**. Parmi les commandes dans la hiérarchie de portée sont **Ajouter un nouvel élément**, **nouvelle requête**, **paramètres du projet**, **Ajouter une nouvelle Source de données**, **lancer l'Assistant Performance**, et **Nouveau diagramme**.  
  
 Commandes dans le **Document** act étendue sur le contenu d'un document, telles que le code, de conception ou d'une requête d'élément de travail \(WIQ\). Également, ils agissent sur l'affichage d'une fenêtre outil ou sont spécifiques à cette fenêtre outil. Commandes de portée document également agiront sur les objets de fichier qui sont eux\-mêmes hiérarchie spécifiques, tels que **Supprimer du projet**. Parmi les commandes dans le document sont étendue **Refactoriser \> Renommer**, **créer une copie de l'élément de travail**, **Développer tout**, **Réduire tout**, et **créer une tâche utilisateur**.  
  
### Décisions de sélection élective de commande  
 Une fois que vous avez décidé de créer une commande, vous devrez déterminer son positionnement appropriée et si vous souhaitez créer un raccourci clavier. Suivez ce chemin de décision pour établir l'emplacement de la commande :  
  
 ![Command placement decision chart](../../extensibility/ux-guidelines/media/0501-a_commandplacement.png "0501\-a\_CommandPlacement")  
  
 **Chemin de décision pour la sélection élective de commande dans Visual Studio**  
  
### Emplacement de la commande dans les menus  
  
#### Barre de menus principale  
 La barre de menus principale doit être l'emplacement standard pour les commandes de tous les packages du menu contextuel spécifiques qui contribuent à l'interface utilisateur. La barre de menus principale est différente des autres structures de commande l'environnement utilise pour contrôler les commandes qui sont visibles. Toutes les autres barres désactiver simplement les commandes qui sortent du cadre, s'ils sont placés dans un menu ou une barre d'outils.  
  
 L'environnement définit un ensemble de commandes intégré à la barre de menus principale qui sont communes à l'IDE entière et plusieurs domaines de la tâche. Ces commandes sont toujours visibles, dont les VSPackages sont chargés dans l'environnement. Bien que les packages VS peuvent étendre cet ensemble de commandes, la commande à partir de chaque produit et le positionnement de leurs commandes est la responsabilité de chaque équipe.  
  
 La structure du menu principal Visual Studio peut être divisée selon les catégories suivantes de menu :  
  
##### Menus principaux  
  
-   Fichier  
  
-   Modifier  
  
-   Afficher  
  
-   Outils  
  
-   Fenêtre  
  
-   Aide  
  
##### Menus spécifiques au projet  
  
-   Projet  
  
-   Build  
  
-   Débogage  
  
##### Menus spécifiques au contexte  
  
-   Équipe  
  
-   Données  
  
-   Test  
  
-   Architecture  
  
-   Analyze  
  
##### Menus spécifiques au document  
  
-   Format  
  
-   Table  
  
##### Lorsque vous concevez des menus principaux, respecter ces règles :  
  
-   Ne pas dépasser 25 éléments de niveau supérieur dans un contexte donné  
  
-   Menus ne doivent jamais dépasser 600 pixels en hauteur.  
  
-   Évaluer un menu principal dans plusieurs contextes, comme dans l'Édition intégrale et le profil général.  
  
-   Menus volants sont acceptables.  
  
-   Menus volants doivent contenir au moins trois éléments et pas plus de sept.  
  
-   Menus volants doivent être qu'un seul niveau de profondeur – certains éléments de menu Visual Studio comportent des sous\-menus en cascade, mais ce modèle n'est pas encouragé.  
  
-   Utilisez des séparateurs pas plus de six. Regroupements doivent respecter l'illustration suivante :  
  
     ![Guidelines for main menu grouping](../../extensibility/ux-guidelines/media/0501-b_mainmenus.png "0501\-b\_MainMenus")  
  
-   Bien que cela n'est pas obligatoire pour que chaque regroupement dans la figure, ajout de regroupements supplémentaires est limitée.  
  
-   Chaque regroupement doit disposer de deux à sept éléments de menu.  
  
#### Commande de menu principal  
 Avant d'ajouter un nouvel élément de niveau supérieur, envisagez de placer la commande dans un menu de niveau supérieur existant. Lorsque vous ajoutez un nouveau menu de niveau supérieur, veillez à placer dans l'emplacement approprié. Décider si le menu est spécifique au projet, contexte ou document. Conservez le nom de menu de niveau supérieur concis et n'utiliser qu'un seul mot.  
  
 Les menus principaux doivent serre\-livres le reste des commandes. Fichier, Édition et affichage doivent toujours à gauche et les outils, fenêtre, et aide doit toujours être vers la droite.  
  
#### Menus contextuels  
 Placer la fonctionnalité de trop dans les menus contextuels se traduit par une interface difficile à apprendre. Toutes les fonctionnalités principales doivent être disponible via la barre de menus principale. Emplacement de la commande doit être harmonisée avec les commandes existantes afin d'éviter les commandes en double. Des menus contextuels, l'interpréteur de commandes définit les groupes de menus standard qui doivent être inclus selon que le menu contextuel est pour la solution, un nœud de projet ou un élément de projet.  
  
 Lorsque vous concevez des menus contextuels, respecter les mêmes règles que pour le menu principal et en outre :  
  
-   Ne dépassez pas 25 éléments de menu de niveau supérieur.  
  
-   Menus volants sont acceptables, mais doit pas dépasser un niveau de profondeur : n'utilisez jamais de lanceurs en cascade.  
  
-   Utilisez des séparateurs pas plus de six.  
  
### Emplacement de la commande dans les barres d'outils  
  
#### Barres d'outils généraux  
 Lors de la conception et de réorganiser les barres d'outils, suivez ces normes :  
  
-   N'utilisez pas plusieurs verbes par bouton. Un bouton \= qu'une seule action.  
  
-   Utiliser le texte à côté de l'icône uniquement si elle doit être complété par une étiquette.  
  
-   Utiliser une zone de liste déroulante exclusivement pour les propriétés qui bascule plusieurs fois dans une session. Exposer dans le cas contraire, la propriété ailleurs.  
  
-   La largeur d'une zone de liste déroulante doit être égale à la largeur de l'élément le plus long dans la zone \+ 30 %. Par exemple, si l'élément le plus long est de 200 pixels, la zone de liste déroulante doit être 260 pixels de large.  
  
-   Limitez l'utilisation de séparateurs. L'utilisation d'un séparateur en regard d'une liste déroulante est un anti\-modèle, étant donné que la forme de la liste déroulante elle\-même agit comme un séparateur visuel.  
  
-   Groupes d'icône doivent contenir de trois à six icônes.  
  
-   Si le résultat de qualificateurs dans plusieurs commandes utiles, utiliser un bouton partagé qui stocke le dernier paramètre :  
  
     ![Split buttons in Visual Studio](../../extensibility/ux-guidelines/media/0501-c_splitbuttons.png "0501\-c\_SplitButtons")  
  
     **Exemple d'un bouton partagé. Les commandes de six à gauche peuvent contenir à la place dans un seul bouton.**  
  
#### Barres d'outils spécifiques au produit  
 Chaque produit peut fournir une valeur par défaut barres d'outils qui contient fréquemment utilisés et des commandes importantes et de chaque produit par défaut doivent s'afficher au premier démarrage de Visual Studio une fois que le produit est installé.  
  
 Produits doivent également exploiter les groupes commande partagé et menus fournis par l'IDE. Chaque groupe de commandes partagé est placé dans un menu partagé permet d'organiser les commandes connexes d'une façon explicite pour l'utilisateur. Il est important de tirer parti de cette structure de commande partagé afin de réduire la complexité.  
  
#### Barres d'outils globales  
 Barres d'outils globales sont requises pour tenir sur une ligne dès. Lorsque vous créez une nouvelle barre d'outils globale, suivez les instructions de ce type de barre d'outils.  
  
 **Instructions générales de barre d'outils :**  
  
-   Chaque barre d'outils a 24 pixels dans les contrôles communs \(barre de redimensionnement, un dépassement de capacité\).  
  
-   Chaque bouton de barre d'outils est 22 pixels de larges, y compris le remplissage. Rendre l'icône d'un bouton partagé ajoute un autre 11 pixels de largeur.  
  
-   Duplication des commandes dans les barres d'outils est autorisée.  
  
 **Barres d'outils spécifiques à** s'affichent lorsqu'un certain type de fichier est actif et disparaissent lorsqu'un autre type de fichier devient actif.  
  
-   Barres d'outils de document spécifique ne peuvent pas avoir plus de 12 boutons.  
  
-   La largeur totale de la barre d'outils ne peut pas dépasser 300 pixels.  
  
-   Chaque type de fichier peut avoir une barre d'outils incorporée ou une barre d'outils globale spécifique au document, mais pas les deux.  
  
 **Barres d'outils contextuelle** apparaissent quand un certain contexte est définie et ont tendance à rester actifs pendant de longues périodes.  
  
-   La limite de bouton pour toutes les barres d'outils contextuelle est 18.  
  
-   Si la plupart des utilisateurs ne sont pas effectivement systématiquement les commandes de la barre d'outils lorsque le contexte est actif, puis n'associer cette barre d'outils à un contexte.  
  
-   Assurez\-vous que la barre d'outils disparaît en quittant le contexte. Aucun de ces barres d'outils doit apparaître au démarrage.  
  
 **Barres d'outils sans contexte** n'apparaissent jamais automatiquement. Ils apparaissent uniquement lorsque l'utilisateur les active. Conserver la largeur maximale ci\-dessous 200 pixels.  
  
### Organisation générale et les groupes définis par l'interpréteur de commandes  
 Utilisez les commandes partagés existants, les groupes de commandes et des menus. Si une nouvelle commande doit être définie, essayez de le placer dans un groupe de commandes partagé existant. Si un nouveau groupe doit être définie, essayez de le placer dans un menu partagé existant proche d'un groupe de commandes connexes avant de créer un nouveau menu de niveau supérieur. Cela réduit la complexité de la commande tout en garantissant le placement de commande cohérente dans l'IDE.  
  
 Le partage **Format** menu, généralement affiché dans le contexte du Concepteur de style de fenêtre de document, est illustré dans l'image suivante :  
  
 ![Visual Studio Format menu with callouts](../../extensibility/ux-guidelines/media/0501-d_formatmenu.png "0501\-d\_FormatMenu")  
  
 **Groupes de menus dans Visual Studio**  
  
### Réduire et réutilisation de commandes  
 Commandes sont généralement indiquées en fonction du contexte, afin de réduire le nombre de commandes de que l'utilisateur voit à un moment donné. Toutefois, vous devez également réutiliser des menus existants partagés et groupes de commande afin de garantir que la structure de commande relativement stable entre les changements de contexte.  
  
 Réutilisation de commandes partagés et placer les nouvelles commandes proche des commandes partagées associées réduit la complexité de l'IDE et crée une expérience plus conviviale.  
  
## Commandes d'affectation de noms  
  
### Conventions d'attribution d'un nom  
 Il est essentiel de commande cohérente d'affectation de noms afin que les utilisateurs peuvent rechercher et exécuter des commandes, soit à l'aide de la ligne de commande ou la liaison à un raccourci clavier. Noms de commande également aider l'utilisateur à quoi une commande sert lorsqu'il est affiché sur une barre d'outils ou dans un menu en cascade ou de contexte.  
  
#### Lorsque des noms commandes :  
  
-   Construire le texte afin qu'elle soit facilement localisable. Pour plus d'informations sur la recherche de texte, consultez [Préparation du monde pour Visual Studio](http://msdn.microsoft.com/fr-fr/1cc35051-8126-441f-bea9-059245a47b1d).  
  
-   Être concis. Les commandes doivent utiliser pas plus de trois mots.  
  
-   Utilisez la casse des mots en majuscule : la première lettre de chaque mot doit être en majuscule. Pour plus d'informations sur la mise en forme dans Visual Studio, consultez [Text style](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).  
  
-   Prenez en compte dans lequel la commande sera placée. Il est dans un menu de niveau supérieur ou un lanceur ? Par exemple, lorsque les commandes d'alignement de regroupement dans un menu volant, les commandes de niveau supérieur doivent être « Alignement » et les commandes de menu volant doit être « Gauche » « Droite », « Center », « Justify » et ainsi de suite. Il serait superflu de nommer les commandes de menu volant « Aligné à gauche » ou « Aligner à droite ».  
  
     ![Visual Studio Format menu](../../extensibility/ux-guidelines/media/0502-a_formatmenu.png "0502\-a\_FormatMenu")  
  
### À l'aide d'icônes avec des commandes  
 À utiliser avec modération de l'utilisation de l'icône de correspondance avec les commandes. Bien que l'association d'une image unique avec une commande accélère grandement la capacité d'utilisateur à identifier cette commande, inefficace et désordre se produisent avec une utilisation abusive de l'image. Les règles suivantes vous aident lorsque vous décidez s'il faut créer une icône de commande.  
  
#### Utilisez une icône avec un commande uniquement si :  
  
-   La même commande possède une icône associée dans un autre produit Microsoft principales, telles que l'une des applications Microsoft Office.  
  
-   La commande sera placée dans une barre d'outils par défaut.  
  
-   La commande est une commande de spécialité que les utilisateurs sont susceptibles d'ajouter une barre d'outils à l'aide de la **« Personnaliser... »** boîte de dialogue.  
  
## Clés d'accès et de raccourci  
  
### Vue d'ensemble  
 Il existe deux types d'affectations de touches de raccourci :  
  
-   **Clés d'accès** \(également appelé accélérateurs\) autoriser l'accès clavier via les menus de commandes et à chaque contrôle label dans la boîte de dialogue interface utilisateur. Touches d'accès sont principalement à des fins d'accessibilité, sont attribués à tous les menus et la plupart des contrôles de boîte de dialogue, ne sont pas destinés à être enregistrés, affectent uniquement la fenêtre active et sont localisés.  
  
-   **Raccourcis** principalement utiliser contrôle \(Ctrl\) et les séquences de touches de fonction \(Fn\). Elles sont conçues plus pour les utilisateurs expérimentés et aide la productivité. Ils sont assignés uniquement à des commandes les plus fréquemment utilisées et permettent un accès rapide en utilisant le menu principal. Touches de raccourci sont destinés à être enregistrés, et pour cette raison doit être affectée cohérent avec le schéma de profil. Schémas de touches de raccourci peuvent varier pour chaque profil. Un utilisateur peut personnaliser les touches de raccourci via **Outils \> Options \> clavier**.  
  
### Affectation des touches d'accès rapide  
 Touches d'accès rapide sont constitués de touches Alt plus alphanumérique. Attribuer une touche d'accès à chaque élément de menu sans exception. Suivez les conventions courantes pour l'affectation des touches d'accès et Windows. par exemple, la clé d'accès pour **fichier \> nouveau** doit toujours être **Alt, F, N**.  
  
 Évitez d'utiliser des lettres de largeur de pixel unique tel que « i » \(en majuscule ou minuscule\) ou un caractère minuscule « l » et évitez d'utiliser des caractères descendants \(g, j, p, q et y\) car ils sont difficiles à distinguer.  
  
 Évitez d'utiliser des clés en double lorsque cela est possible. Dans le cas où la duplication est inévitable, le système de menus gère les conflits en parcourant toutes les commandes qui utilisent la clé. Par exemple, pour un hypothétique de commande dans le menu fichier qui duplique la clé d'accès « N », « Number » **Alt, F, N** serait de créer un nouveau fichier, et **Alt, F, N, N** effectue la commande « Nombre ».  
  
### Affectation des touches de raccourci  
 Évitez d'attribuer de nouvelles touches de raccourci, parce qu'ils ne sont pas requis pour chaque commande et le système \(et la mémoire de l'utilisateur\) de taxe si utilisée de manière excessive. Les données à partir du programme \(amélioration\) indiquent que les utilisateurs de Visual Studio utilisent uniquement un petit sous\-ensemble des raccourcis intégrés.  
  
 Lorsque vous définissez des raccourcis, suivez ces règles :  
  
-   **Utilisez le contrôle \(Ctrl\) et les séquences de touches de fonction \(Fn\).**  
  
-   **Conserver les raccourcis fréquemment utilisés.** Mettre à jour les plus populaires raccourcis.  
  
-   **Faciliter les raccourcis de l'éditeur au type.** Lier les raccourcis vers type aux commandes que les développeurs doivent la plupart lors de l'écriture de code. Par exemple, **Edit.InvokeSmartTag** doit avoir une touche de raccourci rapide comme Ctrl \+ \/ et pas Alt \+ Maj \+ F10.  
  
-   **S'efforcent de raccourcis de façon cohérente à thème.**  
  
-   **Suivez les instructions de Windows pour déterminer quel modificateur de clés à utiliser.** Utilisez les combinaisons de touches Ctrl pour les commandes qui ont des effets à grande échelle, tels que les commandes qui s'appliquent à un document entier. Utiliser les combinaisons de touche MAJ pour étendre ou compléter les actions de la touche de raccourci standard. N'utilisez pas les combinaisons de touches Ctrl \+ Alt.  
  
-   **Supprimer les raccourcis superflues.** Si vous avez une fonctionnalité héritée, envisagez la suppression des raccourcis qui sont utilisés avec extrême mensuelle \(moins de 10 fois dans les données du programme\) ou mensuelle modéré \(moins de 100 fois à partir des données CEIP\) si une clé d'accès fournit un accès rapide à la même commande. Par exemple : Alt, H, C ouvre\/sommaire de l'aide.  
  
 Il n'est pas un moyen simple de vérifier la disponibilité de raccourci. Si vous souhaitez ajouter un raccourci, procédez comme suit :  
  
1.  Vérifiez la liste des [Visual Studio 2013 raccourcis](http://visualstudioshortcuts.com/2013/) pour déterminer s'il existe des commandes semblables aux vôtres avec groupe.  
  
2.  Accédez à **Outils \> Options \> environnement \> clavier** et tester votre raccourci. Vérifiez que chaque schéma de configuration du clavier répertoriés sous « Appliquer le schéma de mappage du clavier ». Vérification des profils général, c\#, VB et C\+\+, comme ceux partagent des raccourcis uniques. Votre raccourci est disponible s'il n'est pas mappé dans un de ces emplacements.