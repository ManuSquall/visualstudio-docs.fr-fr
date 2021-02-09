---
title: Décisions de conception de type de projet | Microsoft Docs
description: Pour plus d’informations sur l’élément, la persistance de fichier projet et les décisions de conception de mécanicien, vous devez prendre des décisions avant d’étendre Visual Studio en créant un nouveau type de projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d1b051abfede6ec90350878f669ed32e7e26b299
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896754"
---
# <a name="project-type-design-decisions"></a>Décisions de conception de type de projet
Avant de créer un nouveau type de projet, vous devez prendre plusieurs décisions de conception concernant votre type de projet. Vous devez décider quels types d’éléments vos projets contiendront, comment les fichiers projet seront rendus persistants et quel modèle d’engagement vous allez utiliser.

## <a name="project-items"></a>Éléments de projet
 Votre projet utilisera-t-il des fichiers ou des objets abstraits ? Si vous utilisez des fichiers, s’agit-il de fichiers basés sur une référence ou d’un répertoire ? Les fichiers ou objets abstraits vont-ils être locaux ou distants ?

 Les éléments d’un projet peuvent être des fichiers, ou ils peuvent être des objets plus abstraits, tels que des objets dans un référentiel de base de données ou des connexions de données sur Internet. Si les éléments sont des fichiers, le projet peut être un projet de référence ou un projet basé sur un répertoire.

 Dans les projets basés sur une référence, les éléments peuvent apparaître dans plusieurs projets. Toutefois, le fichier réel représenté par un élément se trouve dans un seul répertoire. Dans les projets basés sur des répertoires, il existe tous les éléments de projet dans la structure de répertoires.

 Les éléments locaux sont stockés sur l’ordinateur sur lequel l’application est installée. Les éléments distants peuvent être stockés sur un serveur distinct dans un réseau local, ou ailleurs sur Internet.

## <a name="project-file-persistence"></a>Persistance du fichier projet
 Les données seront-elles stockées dans des systèmes de fichiers plats communs ou dans un stockage structuré ? Les fichiers seront-ils ouverts à l’aide d’un éditeur standard ou d’un éditeur spécifique au projet ?

 Pour conserver leurs données, la plupart des applications enregistrent leurs données dans un fichier, puis les relisent lorsqu’un utilisateur doit consulter ou modifier les informations.

 Le stockage structuré, également appelé fichiers composés, est généralement utilisé lorsque plusieurs objets COM (Component Object Model) doivent stocker leurs données persistantes dans un seul fichier. Avec le stockage structuré, plusieurs composants logiciels différents peuvent partager un seul fichier sur disque.

 Vous avez plusieurs options à prendre en compte en matière de persistance pour les éléments de votre projet. Vous pouvez effectuer l’une des options suivantes :

- Enregistrez chaque fichier individuellement lorsqu’il a été modifié.

- Capturer de nombreuses transactions en une seule opération d' **enregistrement** .

- Enregistrez les fichiers localement, puis publiez-les sur un serveur ou utilisez une autre approche pour enregistrer les éléments de projet lorsque l’élément représente une connexion de données à un objet distant.

  Pour plus d’informations sur la persistance, consultez [persistance de projet](../../extensibility/internals/project-persistence.md) et [ouverture et enregistrement d’éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="project-commitment-model"></a>Modèle d’engagement de projet
 Les objets de données persistants seront-ils ouverts en mode direct ou en mode traité ?

 Lorsque les objets de données sont ouverts en mode direct, les modifications apportées aux données sont incorporées immédiatement ou lorsque l’utilisateur enregistre le fichier manuellement.

 Lorsque les objets de données sont ouverts à l’aide du mode traité, les modifications sont enregistrées dans un emplacement temporaire en mémoire et ne sont pas validées tant que l’utilisateur n’a pas choisi manuellement d’enregistrer le fichier. À ce moment-là, toutes les modifications doivent se produire ensemble ou aucune modification n’est apportée.

## <a name="see-also"></a>Voir aussi
- [Checklist : création de types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Ouverture et enregistrement d’éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)
- [Persistance d’un projet](../../extensibility/internals/project-persistence.md)
- [Éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md)
- [Principaux composants d’un modèle de projet](../../extensibility/internals/project-model-core-components.md)
- [Création de types de projets](../../extensibility/internals/creating-project-types.md)
