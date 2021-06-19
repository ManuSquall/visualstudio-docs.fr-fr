---
title: Modéliser l’architecture de votre application &apos;
description: Découvrez comment vous pouvez créer des modèles dans Visual Studio dans le cadre de votre description de la structure et du comportement globaux de votre application ou système logiciel.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fa2be8f4da963c21d9f7f68939421dd7d2d72d0b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390110"
---
# <a name="model-your-app39s-architecture"></a>Modéliser l’architecture de votre application&#39;s
Pour vous assurer que votre application ou votre système logiciel répond aux besoins de vos utilisateurs, vous pouvez créer des modèles dans Visual Studio dans le cadre de votre description de la structure et du comportement globaux de votre application ou de votre système logiciel. Avec des modèles, vous pouvez également décrire des modèles utilisés tout au long de la conception. Ces modèles vous aident à comprendre l'architecture existante, à discuter des modifications et à communiquer clairement vos intentions.

 Pour connaître les éditions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [prise en charge d’édition pour les outils d’architecture et de modélisation](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

 L'objectif d'un modèle est de réduire les ambiguïtés présentes dans les descriptions en langage naturel et de vous aider, vous et vos collègues, à visualiser la conception et à discuter des conceptions alternatives. Un modèle doit être utilisé avec d'autres documents ou discussions. En soi, un modèle ne représente pas une spécification complète de l'architecture.

> [!NOTE]
> Dans cette rubrique, le terme « système » signifie le logiciel que vous développez. Il peut s'agir d'une grande collection de nombreux composants matériels et logiciels, d'une application unique ou d'une partie d'une application.

 L'architecture d'un système peut être divisée en deux parties :

- [Conception de haut niveau](#Structure). Cette section décrit les principaux composants et comment ils interagissent pour répondre à chaque spécification. Si le système est grand, chaque composant peut avoir sa propre conception de haut niveau qui montre comment il est constitué de composants plus petits.

- [Modèles](#Patterns) et conventions de conception utilisés dans les conceptions des composants. Un modèle décrit une approche particulière visant à atteindre un objectif de programmation. En utilisant les mêmes modèles lors de toutes les phases de conception, votre équipe peut réduire le coût des modifications et du développement de nouveaux logiciels.

## <a name="high-level-design"></a><a name="Structure"></a> Conception de haut niveau
 Une conception de haut niveau décrit les principaux composants de votre système et la façon dont ils interagissent pour atteindre les objectifs de la conception. Le développement de la conception de haut niveau implique d'effectuer les activités dans la liste ci-dessous, mais pas nécessairement dans un ordre particulier.

 Si vous mettez à jour du code existant, vous pouvez commencer par décrire les principaux composants. Assurez-vous de bien comprendre les modifications apportées aux besoins des utilisateurs, puis ajoutez ou modifiez les interactions entre les composants. Si vous développez un nouveau système, commencez par comprendre les caractéristiques principales des besoins des utilisateurs. Vous pouvez ensuite explorer des séquences d'interactions pour les cas d'usage principaux, puis consolider les séquences dans une conception de composant.

 Dans tous les cas, il est utile de développer les différentes activités en parallèle et de développer le code et les tests à un stade précoce. N'essayez pas de terminer l'un de ces aspects avant d'en commencer un autre. En règle générale, les impératifs et votre compréhension de la meilleure façon de concevoir le système évolueront pendant l'écriture et les tests du code. Vous devez donc commencer par comprendre et coder les caractéristiques principales des impératifs et de votre conception. Remplissez les détails dans les itérations ultérieures du projet.

- [Comprendre la configuration requise](#Requirements). Le point de départ de toute conception est une vision claire des besoins des utilisateurs.

- [Modèles architecturaux](#BigDecisions). Choix que vous avez effectués concernant les principales technologies et éléments de l'architecture du système.

- Modèle de données des composants et des interfaces. Vous pouvez dessiner des diagrammes de classes pour décrire les informations passées entre les composants et stockées dans les composants.

## <a name="understanding-the-requirements"></a><a name="Requirements"></a> Compréhension des exigences
 Pour développer efficacement la conception de haut niveau d'une application complète, il est préférable de l'associer à un modèle d'impératifs ou autre description des besoins des utilisateurs. Pour plus d’informations sur les modèles d’impératifs, consultez [Configuration requise](../modeling/model-user-requirements.md)pour les utilisateurs.

 Si le système que vous développez est un composant d'un système plus grand, tout ou partie de vos impératifs peuvent être exprimés dans des interfaces de programmation.

 Le modèle d'impératifs fournit les renseignements essentiels suivants :

- Interfaces fournies. Une interface fournie énumère les services ou les opérations que le système ou le composant doit fournir à ses utilisateurs, qu'il s'agisse d'utilisateurs humains ou d'autres composants logiciels.

- Interfaces requises. Une interface requise énumère les services ou les opérations que le système ou le composant peut utiliser. Dans certains cas, vous pourrez concevoir tous ces services dans le cadre de votre propre système. Dans d'autres cas, en particulier si vous concevez un composant qui peut être combiné à d'autres composants dans de nombreuses configurations, l'interface requise sera définie par des considérations externes.

- Impératifs de qualité de service. Objectifs et contraintes de performances, de sécurité, de fiabilité et autres que le système doit satisfaire.

  Le modèle d'impératifs est écrit du point de vue des utilisateurs de votre système, qu'il s'agisse de personnes ou d'autres composants logiciels. Ils ne savent rien des mécanismes internes de votre système. En revanche, votre objectif dans un modèle architectural consiste à décrire les mécanismes internes et à montrer comment ils répondent aux besoins des utilisateurs.

  Avoir des modèles d'impératifs et d'architecture distincts est utile, car cela facilite la discussion des impératifs avec les utilisateurs. Cela aide aussi à refactoriser la conception et à considérer des architectures alternatives tout en laissant les impératifs inchangés.

  La quantité de détails que vous devez mettre dans un modèle d'impératifs ou d'architecture dépend de l'échelle du projet et de la taille et de la distribution de l'équipe. Pour une petite équipe sur un projet de courte durée, le dessin d'un diagramme de classes des concepts métier et de quelques modèles de conception peut suffire. Pour un grand projet distribué sur plusieurs régions, beaucoup plus de détails seront nécessaires.

## <a name="architectural-patterns"></a><a name="BigDecisions"></a> Modèles architecturaux
 Lors de la phase initiale de développement, vous devez choisir les principaux éléments et technologies dont dépend la conception. Ces choix porteront sur les aspects suivants :

- Choix en matière de technologie de base, tels que le choix entre une base de données et un système de fichiers, et le choix entre une application en réseau et un client Web, et ainsi de suite.

- Choix d'infrastructure, tels que le choix entre Windows Workflow Foundation et ADO.NET Entity Framework.

- Choix de méthode d'intégration, par exemple entre un bus de service d'entreprise et un canal point à point.

  Ces choix sont fréquemment déterminés par les impératifs de qualité de service, tels que l'échelle et la flexibilité, et peuvent être effectués avant que les impératifs détaillés soient connus. Dans un système à grande échelle, les configurations matérielle et logicielle sont étroitement liées.

  Vos sélections affectent votre mode d'utilisation et votre interprétation du modèle architectural. Par exemple, dans un système qui utilise une base de données, les associations dans un diagramme de classes peuvent représenter des relations ou des clés étrangères dans la base de données, tandis que dans un système basé sur des fichiers XML, les associations peuvent indiquer des références croisées qui utilisent XPath. Dans un système distribué, les messages figurant dans un diagramme de séquence peuvent représenter des messages sur le câble. Dans une application autonome, ils peuvent représenter des appels de fonction.

## <a name="design-patterns"></a><a name="Patterns"></a> Modèles de conception
 Un modèle de conception est un plan qui décrit comment concevoir un aspect particulier du logiciel, en particulier un aspect qui se reproduit dans différentes parties du système. En adoptant une approche uniforme dans tout le projet, vous pouvez réduire le coût de conception, garantir la cohérence dans l'interface utilisateur et réduire le coût de gestion et de modification du code.

 Certains modèles de conception généraux tels qu'Observer sont bien connus et largement applicables. En outre, il existe des modèles qui sont applicables uniquement à votre projet. Par exemple, dans un système de vente Web, il y aura plusieurs opérations dans le code où des modifications sont apportées à la commande d’un client. Pour vous assurer que l'état de la commande est affiché correctement à chaque étape, toutes ces opérations doivent suivre un protocole particulier pour mettre à jour la base de données.

 Une partie du travail d'architecture logicielle consiste à déterminer quels modèles doivent être adoptés dans toute la conception. Il s'agit généralement d'une tâche continue, car de nouveaux modèles et des améliorations de modèles existants seront découverts à mesure que le projet progresse. Il est utile d'organiser le plan de développement pour que vous puissiez tester chacun de vos principaux modèles de conception à un stade précoce.

 La plupart des modèles de conception peuvent être intégrés en partie dans le code d'infrastructure. Une partie du modèle peut être réduite à obliger le développeur à utiliser des classes ou des composants spécifiques, tels qu'une couche d'accès de base de données qui garantit la gestion correcte de la base de données.

 Un modèle de conception est décrit dans un document et comprend généralement les parties suivantes :

- Nom.

- Description du contexte dans lequel il est applicable. Quels critères doivent inciter un développeur à envisager l'application de ce modèle ?

- Brève explication du problème qu'il résout.

- Modèle des principales parties et de leurs relations. Il peut s'agir de classes ou de composants et d'interfaces, avec des associations et des dépendances entre eux. Les éléments appartiennent généralement à deux catégories :

- Conventions d'attribution de noms.

- Description de la façon dont le modèle résout le problème.

- Description des variations que les développeurs peuvent être en mesure d'adopter.

## <a name="see-also"></a>Voir aussi

- [Visualiser du code](../modeling/visualize-code.md)
- [Modéliser les besoins des utilisateurs](../modeling/model-user-requirements.md)
- [Développer des tests à partir d’un modèle](../modeling/develop-tests-from-a-model.md)
- [Utiliser des modèles dans votre processus de développement](../modeling/use-models-in-your-development-process.md)
