---
title: Visual Studio SDK Glossaire (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 332e606e689e9394f2fcdc8cbc902e2d4a6e5ab5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698168"
---
# <a name="visual-studio-sdk-glossary"></a>Glossaire visual Studio SDK
Ce glossaire fournit des définitions pour [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] les termes qui sont utilisés dans la documentation.

## <a name="terms"></a>Termes
 add-in Une application utilitaire, pilote, ou tout autre logiciel ajouté à une application primaire. Dans l’environnement de développement intégré Visual Studio (IDE), un add-in est une application basée sur l’automatisation qui étend les capacités de l’IDE.

 modèle d’automatisation Le modèle d’automatisation, connu dans les versions précédentes de Visual Studio comme le modèle d’extéabilité, est une interface de programmation qui vous donne accès aux routines sous-jacentes qui conduisent l’IDE. Les add-ins, les assistants et les macros utilisent des objets dans le modèle d’automatisation pour contrôler ou étendre la fonctionnalité de l’IDE.

 commander l’Association du contexte de l’interface utilisateur d’un GUID avec la visibilité d’une commande ou d’un élément d’interface utilisateur tel qu’une barre d’outils. Le contexte de l’interface utilisateur de commande est différent du contexte de sélection en ce qu’il n’est pas attaché à une fenêtre.

 Le contexte de l’interface utilisateur de commande peut être utilisé pour :

- Attribuez un GUID à une barre d’outils qui apparaît lorsqu’une fenêtre particulière est activée.

- Attribuez un GUID à la disponibilité d’une commande sans avoir à charger ou exécuter un VSPackage.

- Attribuer un GUID pour affecter la liaison de clé active.

- Attribuer un GUID pour activer l’enregistrement macro.

- Attribuer un GUID pour activer le mode débogé ou basculer entre la conception et le mode d’exécution dans un éditeur.

  composant Pièce de logiciel qui peut être fait partie de la fonctionnalité d’une application sans que cette application ait des informations préexistantes sur la mise en œuvre du logiciel. La communication entre un composant et une application se fait uniquement par le biais d’interfaces de style OLE.

  service de `SOleComponentManager`coordination des interfaces sans utilisateur pour les composants de haut niveau. Le `SOleComponentManager` service implémente l’interface. `IOleComponentManager`

  composant gestionnaire d’interface `SOleComponentUIManager`utilisateur Un service, qui fournit des services de coordination d’interface utilisateur. Le `SOleComponentUIManager` service implémente les `IOleComponentUIManager` interfaces et `IOleInPlaceComponentUIManager` les interfaces.

  sac contextal Un `IVsUserContext` objet (objet COM) attaché à un composant de l’environnement. Cet objet contient des mots clés de recherche, des mots clés **F1** et des attributs qui se rapportent au composant. Les sacs contextuels indiquent en outre tous les sacs de sous-texte qui y sont liés.

  fournisseur de contexte Un composant dans l’IDE qui a un sac contextuelle qui lui est associé. Ces composants comprennent une fenêtre d’outils, un éditeur ou une hiérarchie de projet.

  concepteur Une interface de programmation qui permet aux utilisateurs de manipuler des éléments de l’interface utilisateur (formes, boutons et autres contrôles).

  DocData Un objet COM encapsulant les données sous-jacentes d’un document dans un monde où il y a séparation de document/vue (par exemple, dans le cas de l’éditeur de texte, ce serait le tampon de texte sous-jacent à toutes les vues de l’éditeur de texte). Si l’Éditeurfact ne fournit pas cet objet, l’IDE en fabrique un en son nom. La responsabilité de cet objet est de gérer la persistance des données `DocData`et la sémantique de partage pour de multiples vues sur ce même . Si `DocData` l’objet `IOleCommandTarget` prend en charge l’interface, il est inclus dans le routage de commande de l’UIShell.

  DocObject Technology avait l’habitude d’héberger l’interface utilisateur dans un cadre fourni par l’hôte. Plus précisément, ce terme fait référence à `IOleDocument` toute intégration qui prend en charge les interfaces et les interfaces connexes. Cette technologie a de nombreuses applications potentielles telles qu’un détail de mise en œuvre de documents COM, des fenêtres d’outils dans Visual Basic 5.0, des concepteurs ActiveX dans Visual Basic 6.0, et ainsi de suite.

  document utilisé pour se référer génériquement au `DocData` document `DocView`dans son ensemble, à la fois le et le . Par exemple, un DocumentFrame contient un `DocView`, mais `DocData` il conserve également une référence à la persistance de manipuler.

  DocView Le DocObject/Embedding/WindowPane avec lequel l’utilisateur interagit pour afficher et manipuler le sous-jacent `DocData`. Les utilisateurs ne profitent pas de la séparation Document/View qui fait partie de la conception de l’interface. `DocObject` Les utilisateurs utilisent un DocObject entier pour agir comme une vue au lieu d’utiliser `DocData`une notion plus abstraite (et moins formalisée) de données sous-jacentes connues sous le nom . `DocView`les objets sont toujours intégrés avec des objets de cadre document (fenêtres d’enfant MDI) de l’IDE.

  DTE `DTE` L’objet (Development Tools Extensibility) est le point d’accès le plus élevé du modèle d’automatisation Visual Studio, qui vous permet d’automatiser et d’étendre l’IDE de manière programmatique.

  Fenêtre Dynamic Help Window Tool qui est implémentée par l’IDE et affiche une liste de mots clés de recherche ou de sujets **F1** Help.

  code d’éditeur (classe, CLSID) qui met en œuvre le `DocView`. Il met `DocData` également en œuvre si la vue et la séparation des données sont prises en charge.

  extension Une fonctionnalité qui modifie, personnalise ou ajoute à un IDE. Vous créez des extensions à l’aide du modèle d’automatisation ou des VSPackages.

  éditeur externe Un éditeur qui n’est pas spécifique à l’IDE, comme Microsoft Word. Il a été enregistré par ses propres mécanismes et peut être utilisé en dehors de l’IDE. Si cet éditeur peut être intégré, il apparaît dans une fenêtre de l’IDE. S’il ne peut pas être intégré, une fenêtre de haut niveau séparée est créée.

  hiérarchie Arbre des nœuds, chaque nœud associé à un ensemble de propriétés.

  composant de haut niveau indépendant A qui utilise une fenêtre de haut niveau sans mode et peut fonctionner efficacement comme une fenêtre d’application autonome, mais qui est implémenté comme objet en cours. Par conséquent, un composant indépendant de haut niveau doit coordonner les services de modalité et de boucle de message avec l’IDE. Les objets en cours n’ont pas leur propre boucle de message.

  fournisseur d’informations Le fournisseur d’informations est un module qui peut rechercher `IVsUserContextItem` des mots clés et retourner une liste de sujets, sous forme d’objets. Pour fournir des éléments de mots-clés **de F1** et de recherche pour le fournisseur d’information, enregistrez votre fichier d’aide compilé (*. HxS*) avec le système. Les sujets d’aide dans ces fichiers fournissent la liste des sujets affichés dans la fenêtre d’aide dynamique et montrent si un utilisateur presse **F1**.

  composant place Un objet VSPackage qui `IOleInPlaceComponent` implémente l’interface pour gérer une fenêtre qui est visuellement contenue dans une fenêtre de document appartenant à l’IDE. Les composants sur place ne participent pas à la fusion standard des menus OLE; au lieu de cela, ils intègrent leurs éléments d’interface utilisateur dans l’IDE.

  Il existe deux types de composants sur place : les composants câblés et les commandes de composants.

  Les composants câblés sur place ont des menus, des barres d’outils et des commandes qui sont étroitement intégrés dans l’interface utilisateur de l’IDE, apparaissant comme s’ils étaient intégrés directement dans l’IDE.

  Les contrôles des composants n’ont aucun de leurs propres éléments d’interface utilisateur intégrés dans l’IDE ; au lieu de cela, ils utilisent les menus, les commandes et les barres d’outils de l’IDE. Par exemple, la commande Bold pourrait être utilisée pour bold un mot sélectionné dans un contrôle de texte riche intégré dans une forme. Toutefois, les contrôles des composants peuvent demander l’affichage d’éléments d’interface utilisateur spécifiques aux composants installés de façon dynamique.

  service linguistique Un ensemble d’objets qui permet aux développeurs de VSPackage de mettre en œuvre des fonctionnalités d’éditeurs de code en langage informatique, telles que le marquage de texte et la colorisation.

  Divers Projet de projet De fichiers utilisés pour héberger des fichiers ouverts qui ne sont pas dans n’importe quel projet. La liste des éléments de ce projet n’est pas persistante.

  projets sont constitués d’objets de hiérarchie, ou d’objets COM qui implémentent l’interface. `IVsHierarchy`

  concepteur ou éditeur spécifique au projet Un designer qui ne peut pas être utilisé indépendamment du type de projet. Tous les concepteurs spécifiques au projet doivent entrer leurs informations Editor Factory dans le registre. L’IDE peut alors instantanéiser le concepteur chaque fois qu’un certain type de fichier est ouvert dans un projet particulier.

  fenêtre de type projet Une fenêtre qui suit constamment la hiérarchie et l’élément du projet actuellement actif à partir du contexte de sélection global. Les fenêtres de `SVsTrackSelectionEx` type projet utilisent le service pour alerter l’IDE des modifications et afficher les commentaires à l’utilisateur. Solution Explorer est un exemple de fenêtre de type projet.

  Fenêtre propriété anciennement Navigateur de propriété.

  projets basés sur des références Projet qui n’exige pas que les fichiers pour le projet soient dans le même répertoire. Au lieu de cela, les références aux fichiers d’autres répertoires non liés sont stockées et maintenues par le projet lui-même.

  tableau de documents structure interne par laquelle l’IDE maintient la liste de tous les documents actuellement ouverts. La liste comprend tous les documents ouverts en mémoire, que les documents soient en cours de modification. Un document est tout élément enregistré, y compris les procédures stockées ouvertes dans un éditeur, les fichiers dans un projet ou le fichier principal du projet (par exemple, le fichier 'vcproj).

  contexte de sélection Données qui font partie du détail de chaque fenêtre de l’IDE et qui sont utilisées pour suivre les sélections actives. Le contexte de sélection se compose de :

- Pointeur `IVsHierarchy` à l’interface de la hiérarchie du projet

- Identifiant d’élément de l’élément du projet.

- Pointeur `ISelectionContainer` à l’interface donnant accès aux propriétés pour les objets actifs.

- Array de valeurs d’éléments.

  service Un contrat pour un ensemble d’interfaces COM qui réside dans un seul objet COM. Lorsque vous créez un service, qui est identifié par un GUID, vous définissez l’ensemble des interfaces COM qui effectuent le service. Les objets COM utilisent les services pour communiquer entre eux.

  solution Groupe de projets connexes avec lesquels un utilisateur travaille.

  concepteur standard Un concepteur qui peut être utilisé indépendamment du type de projet. Tous les concepteurs standard doivent entrer leurs informations Editor Factory dans le registre. L’IDE peut alors instantanéiser le concepteur chaque fois qu’un fichier avec une extension spécifique est ouvert. Les données doivent persister dans un fichier.

  éditeur standard Éditeur qui peut être utilisé indépendamment de n’importe quel type de projet particulier. Ces éditeurs ont EditorFactories enregistré dans le registre. Cela permet à l’IDE de localiser et d’invoquer l’éditeur.

  éditeur D’OS standard Une intégration qui n’est pas spécifique à Visual Studio. Il est enregistré à l’aide des clés Win32 bien connues (par exemple, le Win32 Explorer sait comment invoquer). Si un tel éditeur peut être intégré, l’éditeur apparaît toujours à sa place dans l’IDE. Dans le cas contraire, une fenêtre distincte de haut niveau est créée pour ces éditeurs.

  sac subcontexte Un `IVsUserContext` objet lié à un sac contextuel. L’objet contient des mots clés de recherche, des mots clés **F1** et des attributs pour une sélection dans un composant IDE. Des exemples de sous-texte incluent une commande dans une fenêtre d’outil, ou un mot clé dans un éditeur.

  Liste de tâches Fenêtre d’outil qui est implémentée par l’IDE et affiche une liste de tâches actives.

  texte tampon Nom commun `VSTextBuffer`pour l’objet .

  Vue de texte Nom `VSTextView`commun pour l’objet .

  outil composant haut de gamme Un composant qui fonctionne comme une fenêtre popup sans mode, la coordination étroitement avec l’interface utilisateur de l’IDE. Comme les composants indépendants de haut niveau, les composants de haut niveau des outils doivent également coordonner les services de modalité et de boucle de message avec l’IDE.

  composant haut de gamme Un objet VSPackage qui gère une fenêtre haut de gamme sans mode au lieu de la zone client d’une fenêtre IDE. Les composants de haut `IOleComponent` niveau implémenter l’interface pour tirer parti des services de boucle de message tels que l’accès au temps d’inactivité.

  UI actif Un objet VSPackage qui est visible et a actuellement mise au point.

  Hiérarchie de l’interface un `IVsUIHierarchy` objet COM qui implémente l’interface pour permettre l’affichage d’une hiérarchie. La fenêtre de hiérarchie `ISelectionContainer` de l’interface de l’interface pour mettre à jour la fenêtre Propriétés ; d’autres fenêtres de type projet peuvent utiliser cette implémentation, si désiré.

  Table de commandement de studio visuel VSCT. Le fichier .vsct contient des informations sur le placement et les comportements des menus, des barres d’outils et des commandes en format XML.

  VSPackage Un logiciel installable qui étend l’IDE Visual Studio en contribuant un ou plusieurs des éléments suivants : interface utilisateur, services, types de projets, ou éditeur/concepteur. Un VSPackage se compose d’un `IVsPackage` objet COM qui implémente l’interface et d’un ou plusieurs autres objets COM qui implémentent d’autres interfaces pour prendre en charge la sélection et d’autres fonctionnalités. En outre, un VSPackage a des exigences d’enregistrement spécifiques.
