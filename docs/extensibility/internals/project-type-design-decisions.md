---
title: Décisions de conception de type de projet (en anglais seulement) Microsoft Docs
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e33ac1c4168593b881f799dfdfb94005fb55fc1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706371"
---
# <a name="project-type-design-decisions"></a>Décisions de conception de type de projet
Avant de créer un nouveau type de projet, vous devez prendre plusieurs décisions de conception concernant votre type de projet. Vous devez décider quels types d’éléments vos projets contiendront, comment les fichiers de projet seront persistants et quel modèle d’engagement vous utiliserez.

## <a name="project-items"></a>Éléments de projet
 Votre projet utilisera-t-il des fichiers ou des objets abstraits ? Si vous utilisez des fichiers, s’agira-t-il de fichiers basés sur des références ou des annuaires? Les fichiers ou les objets abstraits seront-ils locaux ou éloignés ?

 Les éléments d’un projet peuvent être des fichiers, ou ils peuvent être des objets plus abstraits tels que des objets dans un référentiel de base de données ou des connexions de données sur Internet. Si les éléments sont des fichiers, le projet peut être soit basé sur des références, soit un projet basé sur l’annuaire.

 Dans les projets basés sur les références, les éléments peuvent apparaître dans plus d’un projet. Toutefois, le fichier réel qu’un élément représente est situé dans un répertoire seulement. Dans les projets d’annuaire, tous les éléments de projet existent dans la structure de l’annuaire.

 Les articles locaux sont stockés sur le même ordinateur où l’application est installée. Les articles distants peuvent être stockés sur un serveur séparé dans un réseau local, ou ailleurs sur Internet.

## <a name="project-file-persistence"></a>Persistance du fichier du projet
 Les données seront-elles stockées dans des systèmes de fichiers plats courants ou dans un stockage structuré ? Les fichiers seront-ils ouverts à l’aide d’un éditeur standard ou d’un éditeur spécifique à un projet ?

 Pour conserver leurs données, la plupart des applications enregistrent leurs données dans un fichier, puis les lisent lorsque l’utilisateur doit examiner ou modifier les informations.

 Le stockage structuré, également appelé fichiers composés, est habituellement utilisé lorsque plusieurs objets du modèle d’objet composant (COM) doivent stocker leurs données persistantes dans un seul fichier. Avec le stockage structuré, plusieurs composants logiciels différents peuvent partager un fichier disque unique.

 Vous avez plusieurs options à considérer en ce qui concerne la persistance des éléments de votre projet. Vous pouvez effectuer l’une des options suivantes :

- Enregistrez chaque fichier individuellement lorsqu’il a été modifié.

- Capturez de nombreuses transactions dans une seule opération **Save.**

- Enregistrez les fichiers localement, puis publiez sur un serveur ou utilisez une autre approche pour enregistrer les éléments du projet lorsque l’élément représente une connexion de données à un objet distant.

  Pour plus d’informations sur la persistance, voir [La persistance du projet](../../extensibility/internals/project-persistence.md) et [l’ouverture et l’économie des éléments du projet](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="project-commitment-model"></a>Modèle d’engagement de projet
 Les objets de données persistants seront-ils ouverts en mode direct ou en mode transigé ?

 Lorsque les objets de données sont ouverts en mode direct, les modifications apportées aux données sont incorporées immédiatement ou lorsque l’utilisateur enregistre manuellement le fichier.

 Lorsque les objets de données sont ouverts en utilisant le mode transigé, les modifications sont enregistrées à un emplacement temporaire dans la mémoire et ne sont pas validées jusqu’à ce que l’utilisateur choisit manuellement d’enregistrer le fichier. À ce moment-là, tous les changements doivent se produire ensemble ou aucun changement ne sera apporté.

## <a name="see-also"></a>Voir aussi
- [Liste de vérification : création de nouveaux types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Ouverture et enregistrement d’éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)
- [Persistance d’un projet](../../extensibility/internals/project-persistence.md)
- [Éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md)
- [Principaux composants d’un modèle de projet](../../extensibility/internals/project-model-core-components.md)
- [Création de types de projets](../../extensibility/internals/creating-project-types.md)
