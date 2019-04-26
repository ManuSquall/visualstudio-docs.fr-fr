---
title: Gestion de version
description: Utilisation de Git et de Subversion dans Visual Studio pour Mac.
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: 0505177e01afd701fe5506df7dd0fc2a2e1f859c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62986522"
---
# <a name="version-control"></a>Gestion de version

La gestion de version est un système de gestion de fichiers sur plusieurs versions auquel contribuent de nombreux développeurs, notamment dans le cadre du développement de logiciels. L’objectif principal d’un système de gestion de version (_VCS_ (Version Control System) est de trouver une solution qui permet à tous les utilisateurs de travailler sur le codebase en même temps.

Au cœur d’un système de gestion de version se trouve un _dépôt_, qui sert de banque de données centrale pour tous les fichiers, à l’instar d’un serveur de fichiers. Toutefois, contrairement à un serveur de fichiers, le dépôt contient l’historique complet du projet et toutes les révisions qui ont été apportées.

Si le dépôt est la banque de données centrale, il est logique que chaque utilisateur dispose d’une banque locale des données pour pouvoir les modifier. Cela s’appelle une _copie de travail_. Dans Visual Studio pour Mac, votre copie de travail s’affiche comme un répertoire local sur votre ordinateur, ce qui vous permet de lire et écrire n’importe quel fichier. Toutefois, parce que Visual Studio pour Mac intègre un système de gestion de version, vous pouvez utiliser Subversion et Git sans quitter l’IDE.

Subversion est un système de gestion de versions centralisé, ce qui signifie qu’il existe un seul serveur contenant tous les fichiers et révisions, à partir duquel les utilisateurs peuvent extraire n’importe quelle version de n’importe quel fichier. Quand les fichiers sont extraits d’un dépôt Subversion distant, l’utilisateur obtient une capture instantanée du dépôt à ce point dans le temps.

Git est un système de gestion de versions distribué qui permet aux équipes de travailler simultanément sur les mêmes documents. Avec Git, il peut exister un seul serveur contenant tous les fichiers, mais l’intégralité du dépôt est clonée localement sur votre machine quand un dépôt est extrait de cette source centrale.

## <a name="basic-concepts"></a>Concepts de base

Visual Studio pour Mac prend en charge les systèmes de gestion de version Git et Subversion. Les articles suivants explorent la configuration des dépôts Git et Subversion dans Visual Studio pour Mac, ainsi que des fonctionnalités simples comme l’examen, la validation et la transmission des modifications.

* [Configuration d’un dépôt Git](set-up-git-repository.md)
* [Utilisation de Git](working-with-git.md)
* [Configuration d’un dépôt Subversion](set-up-subversion-repository.md)
* [Utilisation de Subversion](working-with-subversion.md)

## <a name="see-also"></a>Voir aussi

* [Gestion de versions dans Visual Studio (sur Windows)](/visualstudio/version-control/)