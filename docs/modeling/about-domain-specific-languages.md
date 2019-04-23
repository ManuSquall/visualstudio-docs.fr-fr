---
title: À propos des langages spécifiques à un domaine
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4684a0256e01cafe79fc90ae1ae97dfc2be047d6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60046819"
---
# <a name="about-domain-specific-languages"></a>À propos des langages spécifiques à un domaine

Contrairement à un langage à usage général tel que c# ou UML, un langage spécifique à un domaine (DSL) est conçu pour exprimer des instructions dans un espace de problème particulier, ou un domaine.

DSL Well-Known inclure des expressions régulières et SQL. Chaque DSL est largement préférable à un langage à usage général pour décrire les opérations de chaînes de texte ou une base de données, mais bien pire pour décrire les idées qui sont en dehors de sa propre étendue. Secteurs d’activité individuels ont également leurs propres DSL. Par exemple, dans le secteur des télécommunications, appelez description langues sont couramment utilisées pour spécifier la séquence des États dans un appel téléphonique et en l’air secteur du voyage une norme que DSL est utilisé pour décrire les réservations de vol.

Votre entreprise et votre projet également y spécial des concepts qui peuvent être décrite avec une solution DSL. Par exemple, vous pouvez définir un DSL pour l’une de ces applications :

- Plan des chemins d’accès de navigation dans un site Web.

- Schémas de câblage de composants électroniques.

- Réseaux des tapis roulants et matériel pour un aéroport de manutention de bagages.

Lorsque vous concevez une solution DSL, vous définissez un *de classe de domaine* pour chacun des concepts importants dans le domaine, par exemple une page web, lamp ou aéroport bureau d’enregistrement. Vous définissez *relations de domaine* comme lien hypertexte, câble ou un tapis roulant pour relier les concepts.

Créent des utilisateurs de votre DSL *modèles.* Les modèles sont *instances* du DSL. Par exemple, ils décrivent un site Web particulier, ou le câblage d’un appareil particulier, ou système dans un aéroport particulier de gestion des bagages.

Vos utilisateurs peuvent afficher un modèle sous la forme d’un diagramme ou un formulaire Windows. Modèles peuvent également être affichés en tant que XML, qui est la façon dont ils sont stockés. Lorsque vous définissez un DSL, vous définir comment les instances de chaque classe de domaine et de la relation s’affichent sur l’écran de l’utilisateur. Une solution DSL standard s’affiche comme une collection d’icônes ou les rectangles reliées par des flèches.

La figure suivante illustre un modèle petit dans un DSL schématique :

![Modèle d’arbre généalogique de la famille Tudor](../modeling/media/tudor_familytreemodel.png)

## <a name="what-you-can-do-with-dsls"></a>Ce que vous pouvez faire avec DSL

Une application classique d’une solution DSL consiste à générer du code de programme ou d’autres artefacts. Lorsque vous définissez votre DSL, vous pouvez définir *modèles de texte* qui lire un modèle de la solution DSL et générer des fichiers texte.

Par exemple, vous pouvez écrire des modèles qui prennent un plan de l’aéroport et génèrent une partie du logiciel pour les bagages gérant, ainsi que certains documents utilisateur qui décrivent le plan.

Lorsque vous avez défini un DSL, vous pouvez le distribuer à d’autres utilisateurs qui peuvent l’installer sur leurs propres ordinateurs. Les utilisateurs de votre DSL peuvent créer et modifier des modèles dans Visual Studio.

Vous pouvez également définir des commandes de menu et autres outils qui permettent aux utilisateurs de modifier la solution DSL, les contraintes de validation pour garantir que la solution DSL est utilisé correctement, et les modèles d’élément permettant aux utilisateurs de créent de nouvelles instances. Vous pouvez encapsuler un ou plusieurs DSL avec leurs outils et d’autres extensions de Visual Studio en tant qu’un package intégré.

En règle générale, un langage spécifique à un domaine est créé lorsqu’une équipe de développement doit écrire un code similaire à plusieurs produits. Par exemple, une entreprise spécialisée dans les systèmes de gestion des bagages peut définir un DSL de piste de bagages à partir duquel ils peuvent générer le code pour chaque installation. Les avantages de la solution DSL sont qu’il peuvent être reconnus par leurs clients, que le code généré à partir de celui-ci est fiable, et que le système peut être rapidement mis à jour si vous modifiez des exigences des clients.

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] vous permet de créer un langage spécifique à un domaine qui a votre propre concepteur graphique et vos propres notation de diagramme, puis utiliser le langage pour générer le code source approprié pour chaque projet.

## <a name="domain-specific-development"></a>Développement de spécifique à un domaine

Développement de spécifique à un domaine consiste à identifier les parties de vos applications qui peuvent être modélisées en utilisant un langage spécifique à un domaine et puis construire le langage et son déploiement sur les développeurs d’applications. Les développeurs utilisent le langage spécifique à un domaine pour construire des modèles qui sont spécifiques à leurs applications, utiliser les modèles pour générer du code source, puis utilisez le code source pour développer les applications.

## <a name="aspects-of-graphical-domain-specific-development"></a>Aspects du développement du graphique spécifique à un domaine

Un langage spécifique à un domaine graphique doit inclure les fonctionnalités suivantes :

- Notation

- Modèle de domaine

- Génération de l’artefact

- Sérialisation

- Intégration à Visual Studio

### <a name="notation"></a>Notation

Un langage spécifique à un domaine doit avoir un ensemble relativement peu volumineux d’éléments qui peuvent être définies et étendu pour représentent des constructions spécifiques à un domaine. Une notation se compose de formes, qui représentent les éléments, et de connecteurs, qui représentent les relations entre des éléments, sur une surface de diagramme. Dans [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], les formes peuvent être étendus et affinés pour représenter les éléments de votre langage spécifique à un domaine.

### <a name="domain-model"></a>Modèle de domaine

Un langage spécifique à un domaine doit combiner l’ensemble des éléments et les relations entre eux dans une syntaxe cohérente. Il doit également définir si les combinaisons d’éléments et les relations sont valides. Par exemple, les langages de programmation empêchent généralement l’héritage circulaire, dans laquelle une classe est dérivée d’une classe de la seconde et la deuxième classe est dérivée de la première classe. Contraintes peuvent également être utilisées pour exprimer la logique métier, par exemple, une personne ne peut pas être une dépendance de lui-même. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] utilise des contraintes pour exprimer les types de restrictions qui nécessitent plus des langages spécifiques à un domaine.

### <a name="artifact-generation"></a>Génération de l’artefact

Une des principales finalités d’un langage spécifique à un domaine consiste à générer un artefact, par exemple, code source, un fichier XML ou autres données utilisables. En règle générale, une modification dans le modèle signifie une modification de l’artefact. Vous pouvez utiliser [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] pour générer les artefacts et les régénérer lorsque vous modifiez le modèle.

### <a name="serialization"></a>Sérialisation

Un langage spécifique à un domaine doit être conservé dans une forme qui peut être modifiée, enregistrée, fermée et rechargée. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] utilise un format XML qui vous permet de définir et de personnaliser la façon dont votre langage spécifique à un domaine est sérialisée ou rendues persistantes.

### <a name="integration-with-visual-studio"></a>Intégration à Visual Studio

Étant donné que [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] est hébergé dans Visual Studio, il étend de nombreuses fenêtres Visual Studio et les contrôles. Il vous permet également de personnaliser le comportement des commandes de menu, des éléments de boîte à outils et autres éléments de l’interface utilisateur.

Vous pouvez également créer un adaptateur de Bus de modèle pour votre langage spécifique à un domaine. Cet adaptateur vous permet d’un modèle de référence et des éléments au sein d’un modèle et vous permet de que écrire du code qui peut accéder et mettre à jour une instance du DSL. En utilisant le mécanisme de Bus de modèle puissant, vous pouvez écrire des extensions Visual Studio qui fonctionnent avec plusieurs modèles. Vous pouvez également écrire des applications autonomes qui fonctionnent avec des modèles. Pour plus d’informations, consultez [l’intégration de modèles à l’aide de Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

## <a name="benefits-of-domain-specific-development"></a>Avantages du développement de spécifique à un domaine

Un langage spécifique à un domaine peut fournir les avantages suivants :

- Contient des constructions qui correspondent exactement à l’espace de problème.

     Contrairement aux langages à usage général, un langage spécifique à un domaine se compose d’éléments et les relations qui représentent directement la logique de l’espace de problème. Par exemple, une application d’assurance doit inclure les éléments pour les stratégies et les revendications. Un langage spécifique à un domaine facilite la conception de l’application et de rechercher et de corriger les erreurs de logique.

- Permet de non-développeurs et les personnes qui ne connaissent pas de comprendre la conception globale de domaine.

     En utilisant un langage spécifique à un domaine graphique, vous pouvez créer une représentation visuelle du domaine afin que non-développeurs peuvent facilement comprendre la conception de l’application.

- Facilite la création d’un prototype de l’application finale.

     Les développeurs peuvent utiliser le code qui génère de leur modèle pour créer une application de prototype qu’ils peuvent fournir aux clients.

## <a name="the-process-of-domain-specific-development"></a>Le processus de développement de spécifique à un domaine

La plupart des équipes de développement de logiciels qui utilisent des langages spécifiques à un domaine suivez ces étapes pour créer et utiliser leurs modèles :

- L’équipe distingue les parties variables du domaine à partir des parties qui ne changent jamais.

- Les développeurs d’écrire du code pour les parties fixes et laissent les points d’extension pour les parties variables.

- Le développeur de logiciels senior ou l’architecte crée un langage spécifique à un domaine qui incorpore les modèles de conception des parties fixes du domaine et les points d’extension pour les parties variables.

- Le développeur de logiciels senior ou l’architecte déploie le langage spécifique à un domaine pour les développeurs des diverses applications que l’équipe produit.

- Chaque développeur crée un modèle qui s’applique à l’application spécifique.