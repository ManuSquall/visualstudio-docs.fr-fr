---
title: Vue d’ensemble de GitHub Codespaces (version préliminaire)
description: Apprenez-en davantage sur GitHub Codespaces avec Visual Studio et sur la façon dont il peut vous aider à étendre votre environnement de développement dans le Cloud.
ms.topic: overview
ms.date: 09/04/2020
author: gregvanl
ms.author: gregvanl
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: ab50c3c2df2cfad6d489d800f47624503844dc9d
ms.sourcegitcommit: a667ce8394a800906d633737f4fcbc77f0fcba7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2021
ms.locfileid: "108298741"
---
# <a name="what-is-github-codespaces-preview"></a>Qu’est-ce que GitHub Codespaces ? (Préversion)

> [!Important]
> Depuis le 12 avril 2021, la connexion à GitHub Codespaces à partir de Visual Studio 2019 ne sera plus prise en charge et cette version préliminaire privée s’est terminée. Nous nous concentrons sur les expériences en constante évolution d’une boucle interne basée sur le Cloud et de solutions VDI optimisées pour un large éventail de charges de travail Visual Studio. Nous vous encourageons à participer au [Forum](https://developercommunity.visualstudio.com/home) de la communauté des développeurs pour Visual Studio afin d’obtenir des informations sur les futures versions préliminaires et les informations de feuille de route.

Bienvenue dans Codespaces ! Nous sommes heureux que vous soyez ici.

GitHub Codespaces fournit un environnement de développement basé sur le Cloud pour toutes les activités, qu’il s’agisse d’un projet à long terme ou d’une tâche à long terme telle que la révision d’une demande de tirage (pull request).

En outre, GitHub Codespaces offre un grand nombre des avantages de DevOps, tels que la répétabilité et la fiabilité, &mdash; qui ont généralement été réservés aux charges de travail de production &mdash; dans un environnement de développement. Vous pouvez également personnaliser GitHub Codespaces de sorte que les outils, les processus et les configurations que vous préférez et que vous utilisez soient également là.

Ce document explique les concepts clés et présente les fonctionnalités de Codespaces. Si vous envisagez de commencer, consultez [utiliser Visual Studio avec un codeSpace](use-visual-studio-with-codespaces.md).

## <a name="concepts-and-features"></a>Concepts et fonctionnalités

Les fonctionnalités Codespaces de GitHub sont basées sur quelques concepts fondamentaux. Cette section aborde ces concepts et donne une brève présentation des fonctionnalités.

### <a name="remote-development"></a>Développement à distance

De nombreux développeurs essaient aujourd’hui de coder dans des configurations à distance ou des machines virtuelles configurées avec des piles de développement et d’exécution spécifiques. C’est pourquoi il est trop difficile, trop perturbatrice et, dans certains cas, il est presque impossible de configurer ces environnements de développement localement. En outre, les individus veulent essayer de nouvelles technologies ou de nouvelles infrastructures sans crainte de « dislancer » les machines dont ils ont besoin pour leur travail quotidien.

Bien que l’utilisation d’environnements distants et d’outils distants permette aux développeurs, il y a souvent la surcharge liée à la gestion des ordinateurs. La configuration de l’environnement complique souvent l’intégration et le basculement de contexte. GitHub Codespaces élimine les obstacles à l’intégration rapide et au basculement de contexte en permettant à de nombreux environnements d’exister simultanément.

GitHub Codespaces fournit des solutions gérées qui vous permettent de vous concentrer sur la productivité lors de l’installation. GitHub Codespaces, de manière conceptuelle et techniquement, étend Visual Studio 2019 pour le développement à distance.

### <a name="about-codespaces"></a>À propos de codespaces

Un codeSpace est la moitié « backend » de GitHub Codespaces. C’est là que se trouve tout le calcul associé au développement logiciel : compilation, débogage, restauration, etc. La création d’un codeSpace prépare tout ce dont vous avez besoin pour effectuer une tâche, passer en revue un PR ou démarrer un nouveau projet. Codespaces configurez le runtime, le compilateur, le débogueur, l’éditeur, les configurations dotfile personnalisées et le code source requis pour travailler sur un projet.

Les codespaces hébergés dans le Cloud présentent les avantages suivants :

- Ils sont rapides à créer et à jeter. Créez jusqu’à ce dont vous avez besoin (limites maximales du compte), puis supprimez-les lorsque vous avez terminé.
- Elles sont gérées, ce qui réduit la maintenance globale pour vous.
- Ils ont une tarification prévisible et vous payez uniquement ce que vous utilisez. En outre, il existe une interruption AutoSuspend pour éliminer les coûts d’inéchappement.
- Elles enregistrent des ressources de calcul. Lorsque vous déplacez votre charge de travail de développement vers le Cloud, elle libère les ressources limitées sur votre ordinateur personnel.

## <a name="custom-configuration"></a>Configuration personnalisée

GitHub Codespaces est conçu pour prendre en charge la plus grande variété de projets ou de tâches. Vous pouvez commencer avec les fonctionnalités de configuration intelligente qui fournissent des valeurs par défaut courantes, ou ajuster un codeSpace avec une [configuration personnalisée](customize-codespaces.md).

La configuration flexible permet aux développeurs d’intégrer rapidement des projets avec une configuration et des exigences uniques qui sont difficiles à appliquer sur un ordinateur local. En outre, les codespaces reproductibles éliminent les problèmes « fonctionne sur mon ordinateur ».

## <a name="personal-configuration"></a>Configuration personnelle

Nous savons que la conservation des préférences personnelles est essentielle pour rendre le développement sur une codeSpace hébergée dans le Cloud familière et naturel. GitHub Codespaces couche les personnalisations individualisées par-dessus une configuration codeSpace. Les préférences et la configuration personnelles des éditeurs et des terminaux sont prises en charge par GitHub Codespaces.

Un codeSpace peut être créé avec une collection spécifique à l’utilisateur de [dotfiles personnalisées](https://docs.github.com/github/developing-online-with-codespaces/personalizing-codespaces-for-your-account) (par exemple,, `.bashrc` `.gitconfig` , etc.), et GitHub Codespaces synchronise automatiquement votre identité, vos thèmes et vos paramètres git, de sorte que chaque codeSpace que vous créez se présente comme vous le souhaitez, indépendamment des fonctionnalités d’environnement spécifiques au projet.

## <a name="see-also"></a>Voir aussi

* [Utilisation de Visual Studio avec un codeSpace](use-visual-studio-with-codespaces.md)
* [Comment personnaliser un codeSpace](customize-codespaces.md)
* [Fonctionnalités Visual Studio prises en charge](supported-features-codespaces.md)
