---
title: Glossaire du Kit de développement logiciel Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0a08985c4977896e35fa8cd94014385ac32dd8bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148897"
---
# <a name="visual-studio-sdk-glossary"></a>Glossaire du Kit de développement logiciel Visual Studio
Ce glossaire fournit les définitions des termes utilisés dans le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] documentation.  
  
## <a name="terms"></a>Termes  
 complément  
 Une application de l’utilitaire, pilotes ou autres logiciels ajoutés à un principal de l’application. Dans l’environnement de développement intégré (IDE) de Visual Studio, un complément est une application basée sur l’Automation qui étend les fonctionnalités de l’IDE.  
  
 modèle Automation  
 Le modèle automation, connu dans les versions précédentes de Visual Studio en tant que le modèle d’extensibilité, est une interface de programmation qui vous donne accès aux routines sous-jacentes, ce lecteur de l’IDE. Les compléments, les Assistants et les macros utilisent des objets dans le modèle automation pour contrôler ou étendent les fonctionnalités de l’IDE.  
  
 contexte de l’interface utilisateur de commande  
 Association d’un GUID avec la visibilité d’une commande de l’interface utilisateur ou d’un élément tel qu’une barre d’outils. Contexte de l’interface utilisateur de commande est contrairement au contexte de sélection dans la mesure où il n’est pas attaché à une fenêtre.  
  
 Contexte de l’interface utilisateur de commande peut être utilisé pour :  
  
-   Attribuer un GUID à une barre d’outils qui s’affiche lorsqu’une fenêtre particulière est activée.  
  
-   Attribuer un GUID à la disponibilité d’une commande sans devoir charger ou d’exécuter un VSPackage.  
  
-   Attribuer un GUID pour affecter la liaison de clé active.  
  
-   Attribuer un GUID pour activer l’enregistrement de macro.  
  
-   Attribuer un GUID pour activer le mode de débogage ou pour basculer entre la conception et le mode d’exécution dans un éditeur.  
  
 component  
 Partie d’un logiciel qui peut être effectuée via la fonctionnalité de l’application sans cette application avec toutes les informations existantes sur la mise en œuvre du logiciel. La communication entre un composant et l’application est uniquement par le biais d’interfaces de style OLE.  
  
 Gestionnaire de composants  
 Un service, `SOleComponentManager`, qui fournit des services de coordination de l’interface utilisateur non pour les composants de niveau supérieur. Le `SOleComponentManager` service implémente la `IOleComponentManager` interface.  
  
 Gestionnaire de composants de l’interface utilisateur  
 Un service, `SOleComponentUIManager`, qui fournit des services de coordination d’interface utilisateur. Le `SOleComponentUIManager` service implémente la `IOleComponentUIManager` et `IOleInPlaceComponentUIManager` interfaces.  
  
 conteneur de contexte  
 Un `IVsUserContext` COM (objet) attachée à un composant de l’environnement. Cet objet contient les mots clés de recherche, les mots clés F1 et les attributs qui se rapportent au composant. Sacs de contexte plus point à n’importe quel sacs sous-contexte qui sont liées à elles.  
  
 fournisseur de contexte  
 Un composant dans l’IDE qui possède un jeu de contexte associé. Ces composants incluent une fenêtre outil, un éditeur ou une hiérarchie de projet.  
  
 concepteur  
 Une interface de programmation qui permet aux utilisateurs de manipuler les éléments de l’interface utilisateur (formulaires, boutons et autres contrôles).  
  
 DocData  
 Un objet COM en encapsulant les données sous-jacentes d’un document dans un monde où il existe une séparation de document/vue (par exemple, dans le cas de l’éditeur de texte, cela serait la mémoire tampon de texte sous-jacent de toutes les vues de l’éditeur de texte). Si l’EditorFactory ne fournit pas de cet objet, l’IDE sera fabriquer une sur son nom. Le rôle de cet objet est de gérer la persistance des données et la sémantique de partage de plusieurs vues sur ce même `DocData`. Si le `DocData` objet prend en charge la `IOleCommandTarget` interface, elle sera incluse dans le routage des commandes de la UIShell.  
  
 DocObject  
 Technologie utilisée pour héberger l’interface utilisateur au sein d’une image fournie par l’hôte. Plus spécifiquement, ce terme fait référence à l’incorporation qui prend en charge les `IOleDocument` et les interfaces. Cette technologie a de nombreuses applications potentielles comme un détail d’implémentation de documents de COM, les fenêtres Outil dans Visual Basic 5.0, les concepteurs ActiveX dans Visual Basic 6.0 et ainsi de suite.  
  
 document  
 Utilisé pour désigner le document dans son ensemble, à la fois le `DocData` et `DocView`. Par exemple, un DocumentFrame contient un `DocView`, mais elle conserve également une référence à la `DocData` pour gérer la persistance.  
  
 DocView  
 Le DocObject/Embedding/volet avec lequel l’utilisateur interagit pour afficher et manipuler sous-jacent `DocData`. Notez que les utilisateurs ne tirent pas parti de la séparation de Document/Vue qui fait partie de la `DocObject` conception de l’interface. Les utilisateurs utilisent un ensemble DocObject d’agir en tant que vue au lieu d’utiliser une notion plus abstrait (et moins formalisés) des données sous-jacentes, appelées `DocData`. `DocView` les objets sont toujours incorporées avec des objets Document frame (fenêtres MDI enfants) de l’IDE.  
  
 DTE  
 Le `DTE` les objet (Development Tools Extensibility) sont le point d’accès de plus haut dans le modèle automation de Visual Studio, qui vous permet d’automatiser et étendre l’IDE par programme.  
  
 Fenêtre d’aide dynamique  
 Fenêtre outil qui est implémentée par l’IDE et affiche une liste de mots clés de recherche ou de rubriques d’aide F1.  
  
 éditeur  
 Code (classe, CLSID) qui implémente le `DocView`. Il implémente également `DocData` si la séparation des données d’affichage est prise en charge.  
  
 extension  
 Une fonctionnalité qui modifie, personnalise ou ajoute à un bus IDE. Vous créez des extensions à l’aide du modèle automation ou les VSPackages.  
  
 éditeur externe  
 Un éditeur qui n’est pas spécifique à l’IDE, tel que Microsoft Word. Il a été inscrit par ses propres mécanismes et peut être utilisé en dehors de l’IDE. Si cet éditeur peut être incorporé, il apparaît dans une fenêtre dans l’IDE. S’il ne peut pas être incorporé, une fenêtre de niveau supérieur distincte est créée.  
  
 hiérarchie  
 Arborescence de nœuds, chaque nœud associé à un ensemble de propriétés.  
  
 composant de niveau supérieur indépendant  
 Un composant qui utilise une fenêtre de niveau supérieur non modale et permettre travailler efficacement comme une fenêtre de l’application autonome, mais est implémenté en tant qu’objet dans le processus. Par conséquent, un composant de niveau supérieur indépendant doit coordonner modalité et services de boucle de message avec l’IDE. Objets in-process n’ont pas leur propre boucle de message.  
  
 fournisseur d’informations  
 Le fournisseur d’informations est un module qui peut rechercher des mots clés et retourner une liste de rubriques, sous la forme de `IVsUserContextItem` objets. Pour fournir des éléments de mot clé F1 et de recherche pour le fournisseur d’informations, enregistrez votre fichier d’aide compilé (. HxS) avec le système. Les rubriques d’aide dans ces fichiers sont utilisés pour fournir la liste des rubriques affichées dans la fenêtre Aide dynamique et indiqué si un utilisateur appuie sur F1.  
  
 composant de sur place  
 Un objet VSPackage qui implémente le `IOleInPlaceComponent` interface pour gérer une fenêtre visuellement contenue dans une fenêtre de document détenue par l’IDE. Les composants en place ne participent pas standard OLE-la fusion de menus ; au lieu de cela, ils intègrent leurs éléments d’interface utilisateur dans l’IDE.  
  
 Il existe deux types de composants de la place : non configurable sur place les composants et les contrôles de composant.  
  
 Non configurable sur place composants ont des menus, barres d’outils et les commandes qui sont très bien intégrés dans l’interface utilisateur de l’IDE, qui apparaissent comme si elles ont été créées directement dans l’IDE.  
  
 Les contrôles de composant n’ont pas un de leurs propres éléments d’interface utilisateur intégrés dans l’IDE ; au lieu de cela, ils utilisent les menus, les commandes et les barres d’outils de l’IDE. Par exemple, la commande gras peut servir à afficher en gras d’un mot sélectionné dans un contrôle de texte enrichi incorporé dans un formulaire. Toutefois, les contrôles de composant peuvent demander que les éléments d’interface utilisateur spécifiques à un composant installés dynamiquement affichés.  
  
 Service de langage  
 Un ensemble d’objets qui permet aux développeurs de VSPackage implémenter des fonctionnalités d’éditeurs de code de langue ordinateur, tel que le marquage et la colorisation de texte.  
  
 Projet fichiers divers  
 Projet utilisé pour contenir les fichiers ouverts ne sont pas dans tous les projets. La liste des éléments dans ce projet n’est pas conservée.  
  
 projet  
 Les projets sont constituées d’objets de la hiérarchie, ou des objets COM qui implémentent la `IVsHierarchy` interface.  
  
 Concepteur de projet spécifiques ou un éditeur  
 Un concepteur qui ne peut pas être utilisé indépendamment de type de projet. Tous les concepteurs spécifiques au projet doivent entrer leurs informations de la fabrique d’éditeur dans le Registre. L’IDE peut ensuite instancier le concepteur chaque fois qu’un certain type de fichier est ouvert dans un projet particulier.  
  
 fenêtre de type de projet  
 Une fenêtre qui suit en permanence la hiérarchie de projet actif et d’un élément à partir du contexte de la sélection globale. Type de projet windows utilise le `SVsTrackSelectionEx` service pour alerter l’IDE de modifications et afficher des commentaires à l’utilisateur. L’Explorateur de solutions est un exemple d’une fenêtre de type de projet.  
  
 Fenêtre Propriétés  
 Explorateur de propriétés précédemment.  
  
 projets basés sur une référence  
 Projet qui ne nécessitent pas les fichiers pour le projet dans le même répertoire. Au lieu de cela, les références aux fichiers à partir d’autres annuaires non liées sont stockées et gérées par le projet lui-même.  
  
 table de document en cours d’exécution  
 Structure interne par lequel l’IDE gère la liste de tous les documents actuellement ouverts. Cette liste inclut tous les documents ouverts dans la mémoire, quelle que soit l’indique si les documents sont en cours de modification. Un document est un élément qui est enregistré, y compris les procédures stockées ouvertes dans un éditeur, les fichiers d’un projet ou le fichier projet principal (par exemple, le fichier *.vcproj).  
  
 Contexte de sélection  
 Données qui fait partie du détail de chaque fenêtre dans l’IDE et sont utilisées pour effectuer le suivi de la sélection active. Contexte de sélection comprend :  
  
-   Pointeur vers le `IVsHierarchy` interface de la hiérarchie de projet  
  
-   Identificateur d’élément de l’élément de projet.  
  
-   Pointeur vers le `ISelectionContainer` interface en fournissant l’accès aux propriétés d’objets actifs.  
  
-   Tableau de valeurs d’éléments.  
  
 service  
 Un contrat pour un ensemble d’interfaces COM qui résident dans un objet COM unique. Lorsque vous créez un service, qui est identifié par un GUID, vous définissez le jeu d’interfaces COM qui exécute le service. Objets COM utilisent des services pour communiquer avec un autre.  
  
 Solution  
 Groupe de projets connexes avec laquelle un utilisateur travaille.  
  
 Concepteur standard  
 Un concepteur peut être utilisé indépendamment du type de projet. Tous les concepteurs standards doivent entrer leurs informations de la fabrique d’éditeur dans le Registre. L’IDE peut ensuite instancier le concepteur chaque fois qu’un fichier avec une extension spécifique est ouvert. Les données doivent rendre persistant dans un fichier.  
  
 éditeur standard  
 Éditeur qui peut être utilisé indépendamment de tout type de projet particulier. Ces éditeurs proposent EditorFactories inscrite dans le Registre. Ainsi, l’IDE rechercher et appeler l’éditeur.  
  
 Éditeur du système d’exploitation standard  
 Incorporation qui n’est pas Visual Studio spécifique. Il est enregistré à l’aide des clés connues de Win32 (par exemple, l’Explorateur Win32 sait comment appeler). Si un éditeur de ce type peut être incorporé, l’éditeur s’afficheront toujours dans son emplacement dans l’IDE. Sinon, une fenêtre de niveau supérieur distincte est créée pour ce type d’éditeurs.  
  
 conteneur de sous-contexte  
 Un `IVsUserContext` objet lié à un conteneur de contexte. Cet objet contient les mots clés de recherche, les mots clés F1 et les attributs pour une sélection au sein d’un composant de l’IDE. Exemples de sous-contexte incluent une commande dans une fenêtre outil ou un mot clé dans un éditeur.  
  
 Liste des tâches  
 Fenêtre outil qui est implémentée par l’IDE et affiche une liste de tâches actives.  
  
 Mémoire tampon de texte  
 Nom commun de l’objet `VSTextBuffer`.  
  
 Affichage de texte  
 Nom commun de l’objet `VSTextView`.  
  
 composant de niveau supérieur d’outil  
 Un composant qui fonctionne comme une fenêtre non modale coordination étroitement avec l’interface utilisateur de l’IDE. Comme indépendants des composants de niveau supérieur, composants de niveau supérieur l’outil doivent également coordonner modalité et services de boucle de message avec l’IDE.  
  
 composant de niveau supérieur  
 Un objet VSPackage qui gère une fenêtre non modale de niveau supérieur au lieu de la zone cliente d’une fenêtre de l’IDE. Implémentent des composants de niveau supérieur du `IOleComponent` interface pour tirer parti des services de boucle de message tels que l’accès à la durée d’inactivité.  
  
 Interface utilisateur active  
 Un objet VSPackage qui est visible et qui possède actuellement le focus.  
  
 Hiérarchie de l’interface utilisateur  
 Un objet COM qui implémente le `IVsUIHierarchy` interface pour permettre l’affichage d’une hiérarchie. La fenêtre hiérarchie de l’interface utilisateur implémente la `ISelectionContainer` de l’interface pour mettre à jour de la fenêtre Propriétés ; d’autres fenêtres de type de projet peuvent utiliser cette implémentation, si vous le souhaitez.  
  
 VSCT  
 Table de commandes de Visual Studio. Le fichier .vsct contient des informations sur la sélection élective et les comportements de menus, barres d’outils et des commandes au format XML.  
  
 VSPackage  
 Un élément installable logiciel qui étend l’IDE Visual Studio en ajoutant un ou plusieurs des opérations suivantes : interface utilisateur, les services, les types de projets ou éditeur/concepteur. Un VSPackage se compose d’un objet COM qui implémente le `IVsPackage` interface et un ou plusieurs autres objets COM qui implémentent des autres interfaces pour prendre en charge la sélection et autres fonctionnalités. En outre, un VSPackage a des conditions d’inscription spécifique.