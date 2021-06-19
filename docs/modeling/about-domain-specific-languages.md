---
title: À propos des langages spécifiques à un domaine
description: Découvrez comment un langage spécifique à un domaine (DSL) est conçu pour exprimer des instructions dans un espace de problème ou un domaine particulier.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab56292aafda25efc0b3dfeeb14e93d4502a5567
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384978"
---
# <a name="about-domain-specific-languages"></a>À propos des langages spécifiques à un domaine

Contrairement à un langage à usage général tel que C# ou UML, un langage spécifique à un domaine (DSL) est conçu pour exprimer des instructions dans un espace de problème particulier ou un domaine.

Les DSL bien connus incluent des expressions régulières et SQL. Chaque DSL est bien mieux qu’un langage à usage général pour décrire les opérations sur les chaînes de texte ou une base de données, mais il est bien plus difficile de décrire des idées qui se trouvent en dehors de sa propre portée. Chaque secteur possède également son propre DSL. Par exemple, dans le secteur des télécommunications, les langages de description des appels sont largement utilisés pour spécifier la séquence d’États dans un appel téléphonique et, dans le secteur des voyages aériens, un DSL standard est utilisé pour décrire les réservations de vol.

Votre entreprise et votre projet traitent également de jeux spécifiques de concepts qui peuvent être décrits avec une solution DSL. Par exemple, vous pouvez définir un DSL pour l’une de ces applications :

- Plan des chemins de navigation dans un site Web.

- Diagrammes de câblage pour les composants électroniques.

- Réseaux de tapis roulants et équipement de manutention de bagages pour un aéroport.

Lorsque vous concevez une solution DSL, vous définissez une *classe de domaine* pour chacun des concepts importants dans le domaine, comme une page Web, un éclairage ou un bureau d’enregistrement aéroportuaire. Vous définissez des *relations de domaine* , telles qu’un lien hypertexte, un câble ou un tapis roulant, pour lier les concepts.

Les utilisateurs de votre DSL créent des *modèles.* Les modèles sont des *instances* du DSL. Par exemple, ils décrivent un site Web particulier, ou la connexion d’un appareil particulier, ou le système de gestion des bagages dans un aéroport particulier.

Vos utilisateurs peuvent afficher un modèle sous forme de diagramme ou de formulaire Windows. Les modèles peuvent également être affichés en tant que XML, ce qui est le mode de stockage. Lorsque vous définissez une solution DSL, vous définissez la manière dont les instances de chaque classe et relation de domaine apparaissent sur l’écran de l’utilisateur. Un DSL type est affiché sous la forme d’une collection d’icônes ou de rectangles connectés par des flèches.

L’illustration suivante montre un petit modèle dans un DSL schématique :

![Modèle d'arbre généalogique de la famille Tudor](../modeling/media/tudor_familytreemodel.png)

## <a name="what-you-can-do-with-dsls"></a>Ce que vous pouvez faire avec DSL

Une application classique d’une solution DSL consiste à générer un code de programme ou d’autres artefacts. Lorsque vous définissez votre DSL, vous pouvez définir des *modèles de texte* qui lisent un modèle du DSL et génèrent des fichiers texte.

Par exemple, vous pouvez écrire des modèles qui prennent un plan aéroportuaire et génèrent une partie du logiciel pour la gestion des bagages, ainsi que certains documents utilisateur qui décrivent le plan.

Lorsque vous avez défini une solution DSL, vous pouvez la distribuer à d’autres utilisateurs qui peuvent l’installer sur leurs propres ordinateurs. Les utilisateurs de votre DSL peuvent créer et modifier des modèles dans Visual Studio.

Vous pouvez également définir des commandes de menu et d’autres outils qui aident les utilisateurs à modifier le DSL, les contraintes de validation pour s’assurer que le DSL est utilisé correctement et les modèles d’élément qui aident les utilisateurs à créer de nouvelles instances. Vous pouvez encapsuler un ou plusieurs DSL avec leurs outils et d’autres extensions Visual Studio en tant que package intégré.

En règle générale, un langage spécifique à un domaine est créé lorsqu’une équipe de développement doit écrire du code similaire pour plusieurs produits. Par exemple, une société spécialisée dans les systèmes de gestion des bagages peut définir un DSL de la piste de bagages à partir duquel elle peut générer une partie du code pour chaque installation. Les avantages de la solution DSL sont qu’elle peut être comprise par les clients, que le code généré à partir de celle-ci est fiable et que le système peut être rapidement mis à jour en cas de modification des exigences des clients.

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] vous permet de créer un langage spécifique à un domaine qui contient votre propre concepteur graphique et votre propre notation de diagramme, puis d’utiliser le langage pour générer le code source approprié pour chaque projet.

## <a name="domain-specific-development"></a>Développement Domain-Specific

Le développement spécifique à un domaine est le processus qui consiste à identifier les parties de vos applications qui peuvent être modélisées à l’aide d’un langage spécifique à un domaine, puis à construire le langage et à le déployer pour les développeurs d’applications. Les développeurs utilisent le langage spécifique à un domaine pour construire des modèles spécifiques à leurs applications, utiliser les modèles pour générer le code source, puis utiliser le code source pour développer les applications.

## <a name="aspects-of-graphical-domain-specific-development"></a>Aspects du développement de Domain-Specific graphique

Un langage spécifique à un domaine graphique doit inclure les fonctionnalités suivantes :

- Notation

- Modèle de domaine

- Génération d’artefacts

- Sérialisation

- Intégration à Visual Studio

### <a name="notation"></a>Notation

Un langage spécifique à un domaine doit avoir un ensemble raisonnablement restreint d’éléments qui peuvent être facilement définis et étendus pour représenter des constructions spécifiques à un domaine. Une notation se compose de formes, qui représentent les éléments, et de connecteurs, qui représentent les relations entre les éléments, sur une surface de diagramme graphique. Dans [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , les formes peuvent être étendues et affinées pour représenter les éléments de votre langage spécifique à un domaine.

### <a name="domain-model"></a>Modèle de domaine

Un langage spécifique à un domaine doit combiner l’ensemble d’éléments et les relations entre eux dans une grammaire cohérente. Elle doit également définir si les combinaisons d’éléments et de relations sont valides. Par exemple, les langages de programmation empêchent généralement l’héritage circulaire, dans lequel une classe est dérivée d’une deuxième classe et la deuxième classe est dérivée de la première classe. Les contraintes peuvent également être utilisées pour exprimer la logique métier, par exemple, une personne ne peut pas être une dépendante de lui-même. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] utilise des contraintes pour exprimer les genres de restrictions nécessaires à la plupart des langages spécifiques à un domaine.

### <a name="artifact-generation"></a>Génération d’artefacts

L’un des principaux objectifs d’un langage spécifique à un domaine consiste à générer un artefact, par exemple, un code source, un fichier XML ou d’autres données utilisables. En règle générale, une modification dans le modèle signifie une modification de l’artefact. Vous pouvez utiliser [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] pour générer des artefacts et les régénérer quand vous modifiez le modèle.

### <a name="serialization"></a>Sérialisation

Un langage spécifique à un domaine doit être conservé sous une forme qui peut être modifiée, enregistrée, fermée et rechargée. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] utilise un format XML qui vous permet de définir et de personnaliser la façon dont votre langage spécifique à un domaine est sérialisé ou conservé.

### <a name="integration-with-visual-studio"></a>Intégration à Visual Studio

Étant donné que [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] est hébergé dans Visual Studio, il étend de nombreux contrôles et fenêtres Visual Studio. Elle vous permet également de personnaliser le comportement des commandes de menu, des éléments de boîte à outils et d’autres éléments de l’interface utilisateur.

Vous pouvez également créer un adaptateur de bus de modèles pour votre langage spécifique à un domaine. Cet adaptateur vous permet de référencer un modèle et des éléments dans un modèle, et vous permet d’écrire du code qui peut accéder à une instance du DSL et le mettre à jour. En utilisant le puissant mécanisme de bus de modèle, vous pouvez écrire des extensions Visual Studio qui fonctionnent avec plusieurs modèles. Vous pouvez également écrire des applications autonomes qui fonctionnent avec les modèles. Pour plus d’informations, consultez [intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

## <a name="benefits-of-domain-specific-development"></a>Avantages du développement Domain-Specific

Un langage spécifique à un domaine peut offrir les avantages suivants :

- Contient des constructions qui tiennent exactement dans l’espace du problème.

     Contrairement aux langages à usage général, un langage spécifique à un domaine se compose d’éléments et de relations qui représentent directement la logique de l’espace problématique. Par exemple, une application de stratégie d’assurance doit inclure des éléments pour les stratégies et les revendications. Un langage spécifique à un domaine facilite la conception de l’application et permet de rechercher et de corriger les erreurs de logique.

- Permet aux non-développeurs et aux personnes qui ne connaissent pas le domaine de comprendre la conception globale.

     À l’aide d’un langage spécifique à un domaine graphique, vous pouvez créer une représentation visuelle du domaine afin que les non-développeurs puissent facilement comprendre la conception de l’application.

- Facilite la création d’un prototype de l’application finale.

     Les développeurs peuvent utiliser le code généré par leur modèle pour créer une application prototype qu’ils peuvent afficher aux clients.

## <a name="the-process-of-domain-specific-development"></a>Processus de développement de Domain-Specific

La plupart des équipes de développement de logiciels qui utilisent des langages spécifiques à un domaine suivent les étapes ci-dessous pour créer et utiliser leurs modèles :

- L’équipe distingue les parties variables du domaine des parties qui ne changent jamais.

- Les développeurs écrivent du code pour les parties fixes et laissent des points d’extension pour les parties variables.

- Le développeur de logiciels principal ou l’architecte crée un langage spécifique à un domaine qui incorpore les modèles de conception des parties fixes du domaine et les points d’extension pour les parties variables.

- Le développeur de logiciels principal ou l’architecte déploie le langage spécifique à un domaine pour les développeurs des diverses applications que l’équipe produit.

- Chaque développeur crée un modèle qui s’applique à l’application spécifique.
