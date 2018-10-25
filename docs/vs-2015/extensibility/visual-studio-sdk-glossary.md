---
title: Glossaire du Kit de développement logiciel Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cd23565b5f3bababa16ce5d5d3faa2525bf9a99f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886433"
---
# <a name="visual-studio-sdk-glossary"></a>Glossaire du SDK Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ce glossaire fournit les définitions des termes utilisés dans le [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] documentation.  
  
## <a name="terms"></a>Termes  
 complément  
 Une application utilitaire, pilotes ou autres logiciels ajoutés à une application principale. Dans l’environnement de développement intégré (IDE) de Visual Studio, un complément est une application Automation qui étend les fonctionnalités de l’IDE.  
  
 modèle Automation  
 Le modèle automation, connu dans les versions précédentes de Visual Studio en tant que le modèle d’extensibilité, est une interface de programmation qui vous donne accès aux routines sous-jacentes, ce lecteur de l’IDE. Des compléments, les Assistants et les macros, utilisent des objets dans le modèle automation pour le contrôle ou étendent les fonctionnalités de l’IDE.  
  
 contexte d’interface utilisateur de commande  
 Association d’un GUID avec la visibilité d’une commande d’interface utilisateur ou d’un élément tel qu’une barre d’outils. Contexte d’interface utilisateur de commande diffère de contexte de sélection dans la mesure où il n’est pas attaché à une fenêtre.  
  
 Contexte de l’interface utilisateur de commande peut être utilisé pour :  
  
- Affecter un GUID à une barre d’outils qui s’affiche lorsqu’une fenêtre particulière est activée.  
  
- Affecter un GUID à la disponibilité d’une commande sans avoir à charger ou d’exécuter un VSPackage.  
  
- Affecter un GUID à affecter la combinaison de touches actives.  
  
- Affecter un GUID pour activer l’enregistrement des macros.  
  
- Affecter un GUID pour activer le mode de débogage ou pour basculer entre la conception et le mode d’exécution dans un éditeur.  
  
  component  
  Partie d’un logiciel qui peut être apportée à la partie des fonctionnalités d’une application sans cette application disposant de toutes les informations sur la mise en œuvre du logiciel existantes. La communication entre un composant et une application est uniquement par le biais d’interfaces de style OLE.  
  
  Gestionnaire de composants  
  Un service, `SOleComponentManager`, qui fournit des services de coordination sans interface utilisateur pour les composants de niveau supérieur. Le `SOleComponentManager` service implémente le `IOleComponentManager` interface.  
  
  Gestionnaire de composants de l’interface utilisateur  
  Un service, `SOleComponentUIManager`, qui fournit des services de coordination d’interface utilisateur. Le `SOleComponentUIManager` service implémente le `IOleComponentUIManager` et `IOleInPlaceComponentUIManager` interfaces.  
  
  conteneur de contexte  
  Un `IVsUserContext` COM (objet) attaché à un composant de l’environnement. Cet objet contient les mots clés de recherche, les mots clés F1 et les attributs qui sont liées au composant. De plus, les sacs de contexte point à n’importe quel conteneur de sous-contexte qui est liées à elles.  
  
  fournisseur de contexte  
  Un composant dans l’IDE qui a un sac de contextes associé. Ces composants incluent une fenêtre outil, un éditeur ou une hiérarchie de projet.  
  
  concepteur  
  Interface de programmation qui permet aux utilisateurs de manipuler les éléments de l’interface utilisateur (formulaires, boutons et autres contrôles).  
  
  DocData  
  Un objet COM qui encapsule les données sous-jacentes d’un document dans un monde où séparées de document/vue (par exemple, dans le cas de l’éditeur de texte, ce serait la mémoire tampon sous-jacente de toutes les vues de l’éditeur de texte). Si l’EditorFactory ne fournit pas de cet objet, l’IDE sera fabriquer une en son nom. La responsabilité de cet objet est de gérer la persistance des données et la sémantique de partage de plusieurs vues sur ce même `DocData`. Si le `DocData` objet prend en charge la `IOleCommandTarget` interface, elle sera incluse dans le routage des commandes de la UIShell.  
  
  DocObject  
  Technologie utilisée pour héberger l’interface utilisateur dans une image fournie par l’hôte. Plus précisément, ce terme fait référence à l’incorporation qui prend en charge la `IOleDocument` et d’interfaces associées. Cette technologie a de nombreuses applications potentielles comme un détail d’implémentation de documents de COM, les fenêtres Outil dans Visual Basic 5.0, les concepteurs ActiveX dans Visual Basic 6.0 et ainsi de suite.  
  
  document  
  Utilisé pour désigner le document dans son ensemble, à la fois le `DocData` et `DocView`. Par exemple, un DocumentFrame contient un `DocView`, mais il conserve également une référence à la `DocData` pour gérer la persistance.  
  
  Objet DocView  
  Le DocObject/Embedding/volet de fenêtre avec lequel l’utilisateur interagit pour afficher et manipuler sous-jacent `DocData`. Notez que les utilisateurs ne tirent pas parti de la séparation de Document/Vue qui fait partie de la `DocObject` conception d’interfaces. Les utilisateurs utilisent un ensemble DocObject d’agir en tant que vue au lieu d’utiliser une notion plus abstraite (et moins formalisés) des données sous-jacentes, connu sous le nom `DocData`. `DocView` les objets sont toujours incorporées avec des objets Document frame (fenêtres MDI enfants) de l’IDE.  
  
  DTE  
  Le `DTE` objet (extensibilité d’outils de développement) est le point d’accès de plus haut dans le modèle automation de Visual Studio, ce qui vous permet d’automatiser et étendre l’IDE par programme.  
  
  Fenêtre d’aide dynamique  
  Fenêtre outil qui est implémentée par l’IDE et affiche une liste de mot clé de recherche ou des rubriques d’aide F1.  
  
  éditeur  
  Code (classe, CLSID) qui implémente le `DocView`. Il implémente également `DocData` si la séparation des données d’affichage est pris en charge.  
  
  extension  
  Une fonctionnalité qui modifie, personnalise ou ajoute à un IDE. Vous créez des extensions à l’aide du modèle automation ou les VSPackages.  
  
  éditeur externe  
  Un éditeur qui n’est pas spécifique à l’IDE, tel que Microsoft Word. Il a été inscrit via ses propres mécanismes et peut être utilisé en dehors de l’IDE. Si cet éditeur peut être incorporé, il s’affiche dans une fenêtre dans l’IDE. S’il ne peut pas être incorporé, une fenêtre de niveau supérieur distincte est créée.  
  
  hiérarchie  
  Arborescence de nœuds, chaque nœud associé à un ensemble de propriétés.  
  
  composant de niveau supérieur indépendant  
  Un composant qui utilise une fenêtre de niveau supérieur non modale et peut fonctionner efficacement comme une fenêtre d’application autonome, mais est implémenté comme un objet dans le processus. Par conséquent, un composant indépendant de niveau supérieur doit coordonner modalité et services de boucle de message avec l’IDE. Objets in-process n’ont pas leur propre boucle de message.  
  
  fournisseur d’informations  
  Le fournisseur d’informations est un module qui peut rechercher des mots clés et retourner une liste de rubriques, sous la forme de `IVsUserContextItem` objets. Pour fournir des éléments de mot clé F1 et de recherche pour le fournisseur d’informations, enregistrez votre fichier d’aide compilé (. HxS) avec le système. Les rubriques d’aide dans ces fichiers sont utilisés pour fournir la liste de rubriques affichées dans la fenêtre Aide dynamique et indiqué si un utilisateur appuie sur F1.  
  
  composant de la place  
  Un objet VSPackage qui implémente le `IOleInPlaceComponent` interface pour gérer une fenêtre visuellement contenue dans une fenêtre de document détenue par l’IDE. Déplacement des composants ne participent pas standard-fusion de menus OLE ; au lieu de cela, ils intègrent leurs éléments d’interface utilisateur dans l’IDE.  
  
  Il existe deux types de composants de la place : non configurable sur place les composants et contrôles de composant.  
  
  Non configurable sur place composants ont des menus, barres d’outils et les commandes qui sont étroitement intégrés dans l’interface utilisateur de l’IDE, qui apparaissent comme si elles ont été créées directement dans l’IDE.  
  
  Les contrôles de composant n’ont pas un de leurs propres éléments d’interface utilisateur intégrés dans l’IDE ; elles utilisent plutôt les menus, les commandes et les barres d’outils de l’IDE. Par exemple, la commande en gras peut être utilisée à afficher en gras d’un mot sélectionné dans un contrôle de texte enrichi incorporé dans un formulaire. Toutefois, les contrôles de composant peuvent demander que les éléments d’interface utilisateur spécifiques aux composants installés de manière dynamique affichés.  
  
  service de langage  
  Un ensemble d’objets qui permet aux développeurs de VSPackage implémenter des fonctionnalités d’éditeurs de code de langue ordinateur, telles que du texte de marquage et la colorisation.  
  
  Projet fichiers divers  
  Projet utilisé pour les fichiers ouverts maison qui ne sont pas dans n’importe quel projet. La liste des éléments de ce projet n’est pas conservée.  
  
  projet  
  Les projets sont constituées d’objets de la hiérarchie, ou des objets COM qui implémentent le `IVsHierarchy` interface.  
  
  Concepteur de projet spécifique ou un éditeur  
  Un concepteur qui ne peut pas être utilisé indépendamment de type de projet. Tous les concepteurs spécifiques au projet entre ses informations de la fabrique d’éditeur dans le Registre. L’IDE peut ensuite instancier le concepteur chaque fois qu’un certain type de fichier est ouvert dans un projet particulier.  
  
  fenêtre de type de projet  
  Une fenêtre qui suit en permanence la hiérarchie de projet actif et l’élément à partir du contexte de la sélection globale. Type de projet windows utilise le `SVsTrackSelectionEx` service pour être averti de l’IDE de modifications et afficher des commentaires à l’utilisateur. L’Explorateur de solutions est un exemple d’une fenêtre de type de projet.  
  
  Fenêtre Propriétés  
  Anciennement Explorateur de propriétés.  
  
  Projets basés sur une référence  
  Projet qui ne nécessitent pas les fichiers du projet se trouver dans le même répertoire. Au lieu de cela, les références aux fichiers à partir d’autres répertoires non liées sont stockés et gérés par le projet lui-même.  
  
  table de document en cours d’exécution  
  Structure interne par lequel l’IDE gère la liste de tous les documents actuellement ouverts. Cette liste inclut tous les documents ouverts dans la mémoire indépendamment de si les documents sont en cours de modification. Un document est un élément qui est enregistré, y compris les procédures stockées ouverts dans un éditeur, les fichiers dans un projet ou le fichier projet principal (par exemple, le fichier *.vcproj).  
  
  Contexte de sélection  
  Données qui fait partie du détail de chaque fenêtre dans l’IDE et sont utilisées pour effectuer le suivi des sélections actives. Contexte de sélection se compose de :  
  
- Pointeur vers le `IVsHierarchy` interface de la hiérarchie de projet  
  
- Identificateur d’élément de l’élément de projet.  
  
- Pointeur vers le `ISelectionContainer` interface fournissant l’accès aux propriétés pour les objets actives.  
  
- Tableau de valeurs d’éléments.  
  
  service  
  Un contrat pour un ensemble d’interfaces COM qui se trouvent dans un seul objet COM. Lorsque vous créez un service, qui est identifié par un GUID, vous définissez le jeu d’interfaces COM qui exécute le service. Les objets COM utilisent services pour communiquer entre eux.  
  
  Solution  
  Groupe de projets connexes avec laquelle un utilisateur travaille.  
  
  Concepteur standard  
  Un concepteur qui peut être utilisé indépendamment du type de projet. Tous les concepteurs standards entre ses informations de la fabrique d’éditeur dans le Registre. L’IDE peut ensuite instancier le concepteur chaque fois qu’un fichier avec une extension spécifique est ouvert. Les données doivent rendre persistant dans un fichier.  
  
  éditeur standard  
  Éditeur qui peut être utilisée indépendamment de tout type de projet particulier. Ces éditeurs ont EditorFactories inscrite dans le Registre. Ainsi, l’IDE rechercher et appeler l’éditeur.  
  
  Éditeur du système d’exploitation standard  
  Incorporation qui n’est pas Visual Studio spécifique. Il est inscrit à l’aide des touches Win32 bien connus (par exemple, l’Explorateur Win32 sait comment appeler). Si un éditeur de ce type peut être incorporé, l’éditeur s’afficheront toujours à la place dans l’IDE. Sinon, une fenêtre de niveau supérieur distincte est créée pour ce type d’éditeurs.  
  
  conteneur de sous-contexte  
  Un `IVsUserContext` objet lié à un conteneur de contexte. Cet objet contient les mots clés de recherche, les mots clés F1 et les attributs pour une sélection au sein d’un composant de l’IDE. Exemples de sous-contexte incluent une commande dans une fenêtre outil ou un mot clé dans un éditeur.  
  
  Liste des tâches  
  Fenêtre outil qui est implémentée par l’IDE et affiche une liste de tâches actives.  
  
  Mémoire tampon de texte  
  Nom commun de l’objet `VSTextBuffer`.  
  
  Affichage de texte  
  Nom commun de l’objet `VSTextView`.  
  
  composant de niveau supérieur d’outil  
  Un composant qui fonctionne comme une fenêtre contextuelle non modale, coordination étroitement avec l’interface utilisateur de l’IDE. À l’instar des composants de niveau supérieur indépendants, les composants de niveau supérieur outil doivent coordonner également modalité et services de boucle de message avec l’IDE.  
  
  composant de niveau supérieur  
  Un objet VSPackage qui gère une fenêtre non modale de niveau supérieur au lieu de la zone cliente d’une fenêtre de l’IDE. Implémentent des composants de niveau supérieur du `IOleComponent` interface pour tirer parti des services de boucle de message, comme l’accès à la durée d’inactivité.  
  
  Interface utilisateur active  
  Un objet VSPackage qui est visible et possède actuellement le focus.  
  
  Hiérarchie de l’interface utilisateur  
  Un objet COM qui implémente le `IVsUIHierarchy` interface pour permettre l’affichage d’une hiérarchie. La fenêtre hiérarchie d’interface utilisateur implémente le `ISelectionContainer` pour mettre à jour de la fenêtre Propriétés de l’interface ; d’autres fenêtres de type de projet peuvent utiliser cette implémentation, si vous le souhaitez.  
  
  VSCT  
  Table de commande de Visual Studio. Le fichier .vsct contient des informations sur la position et les comportements de menus, barres d’outils et commandes au format XML.  
  
  VSPackage  
  Un morceau installable de logiciels qui étendent l’IDE Visual Studio en ajoutant un ou plusieurs des opérations suivantes : interface utilisateur, les services, les types de projets ou éditeur/concepteur. Un VSPackage se compose d’un objet COM qui implémente le `IVsPackage` interface et un ou plusieurs autres objets COM qui implémentent les autres interfaces pour prendre en charge la sélection et autres fonctionnalités. En outre, un VSPackage a des conditions d’inscription spécifique.

