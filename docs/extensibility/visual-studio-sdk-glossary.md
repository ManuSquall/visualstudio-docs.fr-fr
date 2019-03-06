---
title: Glossaire du Kit de développement logiciel Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6157b4bc3537a4f88feb91d512241451b8324ba7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682802"
---
# <a name="visual-studio-sdk-glossary"></a>Glossaire de Visual Studio SDK
Ce glossaire fournit les définitions des termes utilisés dans le [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] documentation.

## <a name="terms"></a>Termes
 complément une application utilitaire, pilote ou autres logiciels ajoutés à une application principale. Dans l’environnement de développement intégré (IDE) de Visual Studio, un complément est une application Automation qui étend les fonctionnalités de l’IDE.

 le modèle Automation du modèle automation, connu dans les versions précédentes de Visual Studio en tant que le modèle d’extensibilité, est une interface de programmation qui vous donne accès aux routines sous-jacentes, ce lecteur de l’IDE. Des compléments, les Assistants et les macros, utilisent des objets dans le modèle automation pour le contrôle ou étendent les fonctionnalités de l’IDE.

 contexte d’interface utilisateur de commande Association d’un GUID avec la visibilité d’une commande d’interface utilisateur ou d’un élément tel qu’une barre d’outils. Contexte d’interface utilisateur de commande diffère de contexte de sélection dans la mesure où il n’est pas attaché à une fenêtre.

 Contexte de l’interface utilisateur de commande peut être utilisé pour :

- Affecter un GUID à une barre d’outils qui s’affiche lorsqu’une fenêtre particulière est activée.

- Affecter un GUID à la disponibilité d’une commande sans avoir à charger ou d’exécuter un VSPackage.

- Affecter un GUID à affecter la combinaison de touches actives.

- Affecter un GUID pour activer l’enregistrement des macros.

- Affecter un GUID pour activer le mode de débogage ou pour basculer entre la conception et le mode d’exécution dans un éditeur.

  composant logiciel qui peuvent être apportées à la partie des fonctionnalités d’une application sans cette application disposant de toutes les informations sur la mise en œuvre du logiciel existantes. La communication entre un composant et une application est uniquement par le biais d’interfaces de style OLE.

  service de gestionnaire un composant, `SOleComponentManager`, qui fournit des services de coordination sans interface utilisateur pour les composants de niveau supérieur. Le `SOleComponentManager` service implémente le `IOleComponentManager` interface.

  service de gestionnaire A de l’interface utilisateur de composant, `SOleComponentUIManager`, qui fournit des services de coordination d’interface utilisateur. Le `SOleComponentUIManager` service implémente le `IOleComponentUIManager` et `IOleInPlaceComponentUIManager` interfaces.

  sac de contextes un `IVsUserContext` COM (objet) attaché à un composant de l’environnement. Cet objet contient les mots clés de recherche, **F1** mots clés et des attributs qui se rapportent au composant. De plus, les sacs de contexte point à n’importe quel conteneur de sous-contexte qui est liées à elles.

  composant de fournisseur un contexte dans l’IDE qui a un sac de contextes associé. Ces composants incluent une fenêtre outil, un éditeur ou une hiérarchie de projet.

  Concepteur d’une interface de programmation qui permet aux utilisateurs de manipuler les éléments de l’interface utilisateur (formulaires, boutons et autres contrôles).

  Objet DocData A COM qui encapsule les données sous-jacentes d’un document dans un monde où séparées de document/vue (par exemple, dans le cas de l’éditeur de texte, ce serait la mémoire tampon sous-jacente de toutes les vues de l’éditeur de texte). Si l’EditorFactory ne fournit pas cet objet, l’IDE fabrique un sur son nom. La responsabilité de cet objet est de gérer la persistance des données et la sémantique de partage de plusieurs vues sur ce même `DocData`. Si le `DocData` objet prend en charge la `IOleCommandTarget` interface, il est inclus dans le routage des commandes de la UIShell.

  Technologie de DocObject utilisée pour héberger l’interface utilisateur dans une image fournie par l’hôte. Plus précisément, ce terme fait référence à l’incorporation qui prend en charge la `IOleDocument` et d’interfaces associées. Cette technologie a de nombreuses applications potentielles comme un détail d’implémentation de documents de COM, les fenêtres Outil dans Visual Basic 5.0, les concepteurs ActiveX dans Visual Basic 6.0 et ainsi de suite.

  Utilisé pour désigner le document dans son ensemble de documents, à la fois le `DocData` et `DocView`. Par exemple, un DocumentFrame contient un `DocView`, mais il conserve également une référence à la `DocData` pour gérer la persistance.

  Objet DocView le DocObject/Embedding/volet de fenêtre avec lequel l’utilisateur interagit pour afficher et manipuler sous-jacent `DocData`. Les utilisateurs ne pas tirer parti de la séparation de Document/Vue qui fait partie de la `DocObject` conception d’interfaces. Les utilisateurs utilisent un ensemble DocObject d’agir en tant que vue au lieu d’utiliser une notion plus abstraite (et moins formalisés) des données sous-jacentes, connu sous le nom `DocData`. `DocView` les objets sont toujours incorporées avec des objets Document frame (fenêtres MDI enfants) de l’IDE.

  DTE le `DTE` objet (extensibilité d’outils de développement) est le point d’accès de plus haut dans le modèle automation de Visual Studio, ce qui vous permet d’automatiser et étendre l’IDE par programme.

  Dynamique aide fenêtre outil fenêtre qui est implémentée par l’IDE et affiche une liste de mot clé de recherche ou **F1** rubriques d’aide.

  éditeur de Code (classe, CLSID) qui implémente le `DocView`. Il implémente également `DocData` si la séparation des données et de la vue est pris en charge.

  fonctionnalité d’extension A qui modifie, personnalise ou ajoute à un IDE. Vous créez des extensions à l’aide du modèle automation ou les VSPackages.

  éditeur externe un éditeur qui n’est pas spécifique à l’IDE, tel que Microsoft Word. Il a été inscrit via ses propres mécanismes et peut être utilisé en dehors de l’IDE. Si cet éditeur peut être incorporé, il s’affiche dans une fenêtre dans l’IDE. S’il ne peut pas être incorporé, une fenêtre de niveau supérieur distincte est créée.

  hiérarchie d’arborescence de nœuds, chaque nœud associé à un ensemble de propriétés.

  composant de composant de niveau supérieur indépendant A qui utilise une fenêtre de niveau supérieur non modale et peut fonctionner efficacement comme une fenêtre d’application autonome, mais est implémenté comme un objet dans le processus. Par conséquent, un composant indépendant de niveau supérieur doit coordonner modalité et services de boucle de message avec l’IDE. Objets in-process n’ont leur propre boucle de message.

  fournisseur d’informations le fournisseur d’informations est un module qui peut rechercher des mots clés et retourner une liste de rubriques, sous la forme de `IVsUserContextItem` objets. Pour fournir **F1** et mot clé de recherche des éléments pour le fournisseur d’informations, enregistrez votre fichier d’aide compilé (*. HxS*) avec le système. Les rubriques d’aide dans ces fichiers fournissent la liste des rubriques affichées dans la fenêtre Aide dynamique et indiqué si un utilisateur appuie sur **F1**.

  sur place objet VSPackage d’un composant qui implémente le `IOleInPlaceComponent` interface pour gérer une fenêtre visuellement contenue dans une fenêtre de document détenue par l’IDE. Déplacement des composants ne font pas partie standard-fusion de menus OLE ; au lieu de cela, ils intègrent leurs éléments d’interface utilisateur dans l’IDE.

  Il existe deux types de composants de la place : non configurable sur place les composants et contrôles de composant.

  Non configurable sur place composants ont des menus, barres d’outils et les commandes qui sont étroitement intégrés dans l’interface utilisateur de l’IDE, qui apparaissent comme si elles ont été créées directement dans l’IDE.

  Les contrôles de composant n’ont aucun de leurs propres éléments d’interface utilisateur intégrés dans l’IDE ; elles utilisent plutôt les menus, les commandes et les barres d’outils de l’IDE. Par exemple, la commande en gras peut être utilisée à afficher en gras d’un mot sélectionné dans un contrôle de texte enrichi incorporé dans un formulaire. Toutefois, les contrôles de composant peuvent demander que les éléments d’interface utilisateur spécifiques aux composants installés de manière dynamique affichés.

  langage service un ensemble d’objets qui permet aux développeurs de VSPackage pour implémenter des fonctionnalités de langage informatique des éditeurs de code, telles que du texte de marquage et la colorisation.

  Le projet fichiers divers projet utilisé pour les fichiers ouverts maison qui ne sont pas dans n’importe quel projet. La liste des éléments de ce projet n’est pas conservée.

  Projets de projet sont constituées d’objets de la hiérarchie, ou des objets COM qui implémentent le `IVsHierarchy` interface.

  Concepteur de projet spécifique ou d’éditeur un concepteur qui ne peut pas être utilisé indépendamment de type de projet. Tous les concepteurs spécifiques au projet entre ses informations de la fabrique d’éditeur dans le Registre. L’IDE peut ensuite instancier le concepteur chaque fois qu’un certain type de fichier est ouvert dans un projet particulier.

  type de projet fenêtre une fenêtre qui assure un suivi permanent la hiérarchie de projet actif et l’élément à partir du contexte de la sélection globale. Type de projet windows utilise le `SVsTrackSelectionEx` service pour être averti de l’IDE de modifications et afficher des commentaires à l’utilisateur. L’Explorateur de solutions est un exemple d’une fenêtre de type de projet.

  Anciennement Explorateur de propriétés de la fenêtre Propriétés.

  projets basée sur une référence de projet qui ne nécessite pas les fichiers du projet se trouver dans le même répertoire. Au lieu de cela, les références aux fichiers à partir d’autres répertoires non liées sont stockés et gérés par le projet lui-même.

  structure interne de la table document par lequel l’IDE gère la liste de tous les documents actuellement ouverts en cours d’exécution. La liste inclut tous les documents ouverts dans la mémoire indépendamment de si les documents sont en cours de modification. Un document est un élément qui est enregistré, y compris les procédures stockées ouverts dans un éditeur, les fichiers dans un projet ou le fichier projet principal (par exemple, le fichier *.vcproj).

  contexte de sélection des données qui fait partie du détail de chaque fenêtre dans l’IDE et sont utilisées pour effectuer le suivi des sélections actives. Contexte de sélection se compose de :

- Pointeur vers le `IVsHierarchy` interface de la hiérarchie de projet

- Identificateur d’élément de l’élément de projet.

- Pointeur vers le `ISelectionContainer` interface fournissant l’accès aux propriétés pour les objets actives.

- Tableau de valeurs d’éléments.

  Un contrat pour un ensemble d’interfaces COM qui se trouve dans un objet COM de service. Lorsque vous créez un service, qui est identifié par un GUID, vous définissez le jeu d’interfaces COM qui exécute le service. Les objets COM utilisent services pour communiquer entre eux.

  solution de groupe de projets connexes avec laquelle un utilisateur travaille.

  Un concepteur qui peut être utilisé indépendamment du type de projet de concepteur standard. Tous les concepteurs standards entre ses informations de la fabrique d’éditeur dans le Registre. L’IDE peut ensuite instancier le concepteur chaque fois qu’un fichier avec une extension spécifique est ouvert. Les données doivent rendre persistant dans un fichier.

  standard éditeur qui peuvent être utilisées indépendamment de tout type de projet particulier. Ces éditeurs ont EditorFactories inscrite dans le Registre. Ainsi, l’IDE rechercher et appeler l’éditeur.

  Éditeur du système d’exploitation standard incorporation qui n’est pas spécifique de Visual Studio. Il est inscrit à l’aide des touches Win32 bien connus (par exemple, l’Explorateur Win32 sait comment appeler). Si un éditeur de ce type peut être incorporé, l’éditeur apparaît dans sa place dans l’IDE. Sinon, une fenêtre de niveau supérieur distincte est créée pour ce type d’éditeurs.

  conteneur de sous-contexte un `IVsUserContext` objet lié à un conteneur de contexte. L’objet conserve les mots clés de recherche, **F1** mots clés et des attributs pour une sélection au sein d’un composant de l’IDE. Exemples de sous-contexte incluent une commande dans une fenêtre outil ou un mot clé dans un éditeur.

  Fenêtre liste des tâches outil qui est implémentée par l’IDE et affiche une liste de tâches actives.

  nom commun de texte mémoire tampon pour l’objet `VSTextBuffer`.

  Nom commun de vue de texte pour l’objet `VSTextView`.

  composant de composant de niveau supérieur un outil qui fonctionne comme une fenêtre contextuelle non modale, coordination étroitement avec l’interface utilisateur de l’IDE. À l’instar des composants de niveau supérieur indépendants, les composants de niveau supérieur outil doivent coordonner également modalité et services de boucle de message avec l’IDE.

  objet d’un VSPackage de composant de niveau supérieur qui gère une fenêtre non modale de niveau supérieur au lieu de la zone cliente d’une fenêtre de l’IDE. Implémentent des composants de niveau supérieur du `IOleComponent` interface pour tirer parti des services de boucle de message, comme l’accès à la durée d’inactivité.

  Active un VSPackage objet d’interface utilisateur qui est visible et possède actuellement le focus.

  L’interface utilisateur hiérarchie COM d’un objet qui implémente le `IVsUIHierarchy` interface pour permettre l’affichage d’une hiérarchie. La fenêtre hiérarchie d’interface utilisateur implémente le `ISelectionContainer` pour mettre à jour de la fenêtre Propriétés de l’interface ; d’autres fenêtres de type de projet peuvent utiliser cette implémentation, si vous le souhaitez.

  VSCT Visual Studio Command Table. Le fichier .vsct contient des informations sur la position et les comportements de menus, barres d’outils et commandes au format XML.

  VSPackage un morceau installable de logiciels qui étendent l’IDE Visual Studio en ajoutant un ou plusieurs des éléments suivants : interface utilisateur, les services, les types de projets ou éditeur/concepteur. Un VSPackage se compose d’un objet COM qui implémente le `IVsPackage` interface et un ou plusieurs autres objets COM qui implémentent les autres interfaces pour prendre en charge la sélection et autres fonctionnalités. En outre, un VSPackage a des conditions d’inscription spécifique.