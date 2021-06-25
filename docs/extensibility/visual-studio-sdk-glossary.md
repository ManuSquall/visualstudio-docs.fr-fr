---
title: Glossaire du SDK Visual Studio | Microsoft Docs
description: Ce glossaire fournit des définitions pour les termes utilisés dans la documentation du kit de développement logiciel (SDK) Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 49e91a64220882eea196819a1860052dc871bec4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905421"
---
# <a name="visual-studio-sdk-glossary"></a>Glossaire du SDK Visual Studio
Ce glossaire fournit des définitions pour les termes utilisés dans la [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] documentation.

## <a name="terms"></a>Termes
 complément d’une application utilitaire, d’un pilote ou d’un autre logiciel ajouté à une application principale. Dans l’environnement de développement intégré (IDE) de Visual Studio, un complément est une application Automation qui étend les fonctionnalités de l’IDE.

 modèle Automation le modèle Automation, connu dans les versions précédentes de Visual Studio en tant que modèle d’extensibilité, est une interface de programmation qui vous donne accès aux routines sous-jacentes qui pilotent l’IDE. Les compléments, les assistants et les macros utilisent des objets dans le modèle Automation pour contrôler ou étendre les fonctionnalités de l’IDE.

 Association de contexte d’interface utilisateur de commande d’un GUID avec la visibilité d’une commande ou d’un élément d’interface utilisateur tel qu’une barre d’outils. Le contexte de l’interface utilisateur de commande est différent du contexte de sélection, car il n’est pas attaché à une fenêtre.

 Le contexte de l’interface utilisateur de commande peut être utilisé pour :

- Assignez un GUID à une barre d’outils qui apparaît lorsqu’une fenêtre particulière est activée.

- Assigner un GUID à la disponibilité d’une commande sans avoir à charger ou exécuter un VSPackage.

- Assigner un GUID pour affecter la liaison de clé active.

- Attribuez un GUID pour activer l’enregistrement des macros.

- Assignez un GUID pour activer le mode débogage ou pour basculer entre le mode création et le mode exécution dans un éditeur.

  Élément logiciel qui peut faire partie des fonctionnalités d’une application sans que cette application n’ait d’informations préexistantes sur l’implémentation du logiciel. La communication entre un composant et une application s’effectue uniquement par le biais d’interfaces de style OLE.

  Gestionnaire de composants un service, `SOleComponentManager` , qui fournit des services de coordination d’interface non utilisateur pour les composants de niveau supérieur. Le `SOleComponentManager` service implémente l' `IOleComponentManager` interface.

  Component UI Manager un service, `SOleComponentUIManager` , qui fournit des services de coordination de l’interface utilisateur. Le `SOleComponentUIManager` service implémente les `IOleComponentUIManager` `IOleInPlaceComponentUIManager` interfaces et.

  conteneur de contexte `IVsUserContext` objet (objet com) attaché à un composant d’environnement. Cet objet contient les mots clés de recherche, les mots clés **F1** et les attributs liés au composant. Les conteneurs de contexte pointent également vers tous les conteneurs de sous-contexte qui y sont liés.

  fournisseur de contexte composant dans l’IDE auquel est associé un sac de contexte. Ces composants incluent une fenêtre outil, un éditeur ou une hiérarchie de projet.

  concepteur interface de programmation qui permet aux utilisateurs de manipuler des éléments de l’interface utilisateur (formulaires, boutons et autres contrôles).

  DocData un objet COM encapsulant les données sous-jacentes d’un document dans un monde où il existe une séparation document/vue (par exemple, dans le cas de l’éditeur de texte, il s’agit de la mémoire tampon de texte sous-jacente de toutes les vues de l’éditeur de texte). Si le EditorFactory ne fournit pas cet objet, l’IDE en fabrique un en son nom. La responsabilité de cet objet est de gérer la persistance des données et la sémantique de partage pour plusieurs vues sur ce même `DocData` . Si l' `DocData` objet prend en charge l' `IOleCommandTarget` interface, il est inclus dans le routage des commandes du uiShell.

  Technologie DocObject utilisée pour héberger l’interface utilisateur dans un frame fourni par l’hôte. Plus précisément, ce terme fait référence à toute incorporation qui prend en charge les `IOleDocument` interfaces et associées. Cette technologie a de nombreuses applications potentielles, telles que le détail d’implémentation des documents COM, les fenêtres outil dans Visual Basic 5,0, les concepteurs ActiveX dans Visual Basic 6,0, etc.

  document utilisé pour faire référence de manière générique au document dans son ensemble, à la fois le `DocData` et le `DocView` . Par exemple, un DocumentFrame contient un `DocView` , mais il conserve également une référence au `DocData` pour gérer la persistance.

  DocView : DocObject/Embedding/volet de fenêtre avec lequel l’utilisateur interagit pour afficher et manipuler le sous-jacent `DocData` . Les utilisateurs ne tirent pas parti de la séparation du document/de la vue qui fait partie de la conception de l' `DocObject` interface. Les utilisateurs utilisent un DocObject entier pour agir en tant que vue au lieu d’utiliser une notion plus abstraite (et moins formalisée) de données sous-jacentes, connue sous le nom de `DocData` . `DocView` les objets sont toujours incorporés avec les objets de cadre de document (fenêtres enfants MDI) de l’IDE.

  DTE l' `DTE` objet (extensibilité des outils de développement) est le point d’accès le plus élevé dans le modèle Automation de Visual Studio, qui vous permet d’automatiser et d’étendre par programmation l’IDE.

  Fenêtre outil de fenêtre d’aide dynamique qui est implémentée par l’IDE et qui affiche une liste de mots clés de recherche ou des rubriques d’aide **F1** .

  Code de l’éditeur (classe, CLSID) qui implémente `DocView` . Il implémente également `DocData` si la vue et la séparation des données sont prises en charge.

  extension fonctionnalité qui modifie, personnalise ou ajoute à un IDE. Vous créez des extensions à l’aide du modèle Automation ou de VSPackages.

  éditeur externe un éditeur qui n’est pas spécifique à l’environnement de développement intégré (IDE), tel que Microsoft Word. Il a été enregistré à l’aide de ses propres mécanismes et peut être utilisé en dehors de l’IDE. Si cet éditeur peut être incorporé, il apparaît dans une fenêtre de l’IDE. S’il ne peut pas être incorporé, une fenêtre de niveau supérieur distincte est créée.

  Arborescence hiérarchique des nœuds, chaque nœud associé à un ensemble de propriétés.

  composant de niveau supérieur indépendant un composant qui utilise une fenêtre de niveau supérieur non modal et peut fonctionner efficacement comme une fenêtre d’application autonome, mais il est implémenté en tant qu’objet in-process. Par conséquent, un composant de niveau supérieur indépendant doit coordonner la modalité et les services de boucle de message avec l’IDE. Les objets in-process n’ont pas leur propre boucle de message.

  fournisseur d’informations le fournisseur d’informations est un module qui peut rechercher des mots clés et retourner une liste de rubriques, sous la forme d' `IVsUserContextItem` objets. Pour fournir des éléments de mot clé **F1** et de recherche pour le fournisseur d’informations, inscrivez votre fichier d’aide compilé (*. HxS*) avec le système. Les rubriques d’aide de ces fichiers fournissent la liste des rubriques affichées dans la fenêtre aide dynamique et indiquent si un utilisateur appuie sur la **touche F1**.

  composant sur place objet VSPackage qui implémente l' `IOleInPlaceComponent` interface pour gérer une fenêtre contenue visuellement dans une fenêtre de document détenue par l’IDE. Les composants sur place ne participent pas à la fusion de menus OLE standard. au lieu de cela, ils intègrent leurs éléments d’interface utilisateur dans l’IDE.

  Il existe deux types de composants sur place : les composants sur place câblés et les contrôles de composants.

  Les composants sur place intègrent des menus, des barres d’outils et des commandes qui sont étroitement intégrés à l’interface utilisateur de l’IDE, qui apparaissent comme s’ils étaient intégrés directement dans l’IDE.

  Les contrôles de composants n’ont aucun de leurs propres éléments d’interface utilisateur intégrés dans l’IDE ; au lieu de cela, ils utilisent les menus, les commandes et les barres d’outils de l’IDE. Par exemple, la commande en gras peut être utilisée pour mettre en gras un mot sélectionné dans un contrôle de texte enrichi incorporé dans un formulaire. Toutefois, les contrôles de composants peuvent demander l’affichage des éléments d’interface utilisateur spécifiques à un composant.

  service de langage un ensemble d’objets qui permet aux développeurs VSPackage d’implémenter des fonctionnalités d’éditeurs de code de langue informatique, tels que le marquage de texte et la coloration.

  Fichier de projet fichiers divers utilisé pour héberger des fichiers ouverts qui ne se trouvent dans aucun projet. La liste des éléments de ce projet n’est pas persistante.

  les projets de projet sont constitués d’objets de hiérarchie, ou d’objets COM qui implémentent l' `IVsHierarchy` interface.

  concepteur ou éditeur spécifique à un projet qui ne peut pas être utilisé indépendamment du type de projet. Tous les concepteurs spécifiques au projet doivent entrer leurs informations de fabrique d’éditeur dans le registre. L’IDE peut ensuite instancier le concepteur chaque fois qu’un certain type de fichier est ouvert dans un projet particulier.

  fenêtre de type projet une fenêtre qui effectue en permanence le suivi de la hiérarchie de projet et de l’élément actuellement actifs dans le contexte de sélection globale. Les fenêtres de type de projet utilisent le `SVsTrackSelectionEx` service pour alerter l’IDE des modifications et pour afficher des commentaires à l’utilisateur. Explorateur de solutions est un exemple de fenêtre de type projet.

  Fenêtre Propriétés ancien Explorateur de propriétés.

  projets basés sur des références qui ne nécessitent pas que les fichiers du projet se trouvent dans le même répertoire. Au lieu de cela, les références à des fichiers provenant d’autres répertoires non liés sont stockées et gérées par le projet lui-même.

  exécution de la structure interne de la table de documents par laquelle l’IDE gère la liste de tous les documents actuellement ouverts. La liste comprend tous les documents ouverts en mémoire, que les documents soient actuellement modifiés ou non. Un document est un élément enregistré, y compris des procédures stockées ouvertes dans un éditeur, des fichiers dans un projet ou le fichier projet principal (par exemple, le fichier *. vcproj).

  Données de contexte de sélection qui font partie des détails de chaque fenêtre de l’IDE et sont utilisées pour effectuer le suivi des sélections actives. Le contexte de sélection se compose des éléments suivants :

- Pointeur vers l' `IVsHierarchy` interface de la hiérarchie de projet

- Identificateur d’élément de l’élément de projet.

- Pointeur vers l' `ISelectionContainer` interface qui fournit l’accès aux propriétés des objets actifs.

- Tableau de valeurs d’éléments.

  traiter un contrat pour un ensemble d’interfaces COM qui réside dans un objet COM unique. Lorsque vous créez un service, identifié par un GUID, vous définissez l’ensemble des interfaces COM qui exécutent le service. Les objets COM utilisent des services pour communiquer les uns avec les autres.

  Groupe de solutions de projets associés avec lesquels un utilisateur travaille.

  concepteur standard concepteur qui peut être utilisé indépendamment du type de projet. Tous les concepteurs standard doivent entrer leurs informations de fabrique d’éditeur dans le registre. L’IDE peut ensuite instancier le concepteur chaque fois qu’un fichier avec une extension spécifique est ouvert. Les données doivent être conservées dans un fichier.

  Éditeur de l’éditeur standard qui peut être utilisé indépendamment d’un type de projet particulier. De tels éditeurs ont EditorFactories inscrit dans le registre. Cela permet à l’IDE de localiser et d’appeler l’éditeur.

  éditeur de système d’exploitation standard incorporé qui n’est pas spécifique à Visual Studio. Elle est inscrite à l’aide des clés Win32 connues (par exemple, l’Explorateur Win32 sait comment appeler). Si un tel éditeur peut être incorporé, l’éditeur s’affiche toujours à sa place dans l’IDE. Dans le cas contraire, une fenêtre de niveau supérieur distincte est créée pour ces éditeurs.

  conteneur de sous-contexte `IVsUserContext` objet lié à un conteneur de contexte. L’objet contient les mots clés de recherche, les mots clés **F1** et les attributs d’une sélection dans un composant IDE. Les exemples de sous-contexte incluent une commande dans une fenêtre outil ou un mot clé dans un éditeur.

  Fenêtre outil de liste des tâches qui est implémentée par l’IDE et affiche la liste des tâches actives.

  nom commun de la mémoire tampon de texte pour l’objet `VSTextBuffer` .

  Nom commun de l’affichage de texte pour l’objet `VSTextView` .

  composant de niveau supérieur de l’outil composant qui fonctionne comme une fenêtre contextuelle non modale, en coordonnant étroitement avec l’interface utilisateur de l’IDE. À l’instar des composants de niveau supérieur indépendants, les composants de niveau supérieur de l’outil doivent également coordonner la modalité et les services de boucle de message avec l’IDE.

  composant de niveau supérieur objet VSPackage qui gère une fenêtre de niveau supérieur non modale au lieu de la zone cliente d’une fenêtre IDE. Les composants de niveau supérieur implémentent l' `IOleComponent` interface pour tirer parti des services de boucle de message, tels que l’accès au temps d’inactivité.

  UI active un objet VSPackage qui est visible et qui a actuellement le focus.

  Hiérarchie d’interface utilisateur objet COM qui implémente l' `IVsUIHierarchy` interface pour permettre l’affichage d’une hiérarchie. La fenêtre hiérarchie d’interface utilisateur implémente l' `ISelectionContainer` interface pour mettre à jour le fenêtre Propriétés ; d’autres fenêtres de type projet peuvent utiliser cette implémentation, si vous le souhaitez.

  Table de commandes Visual Studio VSCT. Le fichier. vsct contient des informations sur le positionnement et les comportements des menus, des barres d’outils et des commandes au format XML.

  VSPackage un logiciel pouvant être installé et qui étend l’IDE de Visual Studio en contribuant au moins l’un des éléments suivants : interface utilisateur, services, types de projets ou éditeur/concepteur. Un VSPackage se compose d’un objet COM qui implémente l' `IVsPackage` interface et d’un ou plusieurs autres objets COM qui implémentent d’autres interfaces pour prendre en charge la sélection et d’autres fonctionnalités. En outre, un VSPackage a des exigences d’inscription spécifiques.
