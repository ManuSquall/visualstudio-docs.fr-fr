---
title: Les décisions de conception de Type de projet | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c28c6f29454feed94407d6e37c3432247b9a4a26
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="project-type-design-decisions"></a>Décisions de conception de Type de projet
Avant de créer un nouveau type de projet, vous devez prendre des décisions de conception plusieurs concernant votre type de projet. Vous devez décider quels types d’éléments de vos projets, mode de conservation des fichiers projet et quel modèle d’engagement que vous allez utiliser.  
  
## <a name="project-items"></a>Éléments de projet  
 Votre projet utilise les fichiers ou objets abstraits ? Si vous utilisez des fichiers, sera-t-il fichiers basée sur le répertoire ou référence ? Sont des fichiers ou des objets abstraits avenir soit local ou distant ?  
  
 Les éléments d’un projet peuvent être des fichiers, ou ils peuvent être plus abstraites tels que les objets dans une connexion de données ou le référentiel de base de données sur Internet. Si les éléments sont des fichiers, le projet peut être basée sur une référence ou un projet basé sur le répertoire.  
  
 Dans les projets de base de référence, les éléments peuvent apparaître dans plusieurs projets. Toutefois, le fichier réel représentant un élément se trouve dans un répertoire uniquement. Dans les projets basée sur Active, tous les éléments de projet existent dans la structure de répertoires.  
  
 Les éléments locaux sont stockés sur le même ordinateur que celui où l’application est installée. Les éléments à distance peuvent être stockées sur un serveur distinct dans un réseau local, ou un autre emplacement sur Internet.  
  
## <a name="project-file-persistence"></a>Persistance d’un fichier projet  
 Données être stockées dans des systèmes de fichiers plats courants, ou dans le stockage structuré ? Fichiers seront être ouvert à l’aide d’un éditeur standard ou un éditeur spécifique au projet ?  
  
 Pour conserver leurs données, la plupart des applications enregistrent leurs données dans un fichier et puis de le lire lorsqu’un utilisateur doit examiner ou modifier les informations.  
  
 Stockage structuré, également appelé fichiers composés, est généralement utilisé lorsque vous avez besoin de plusieurs objets de modèle COM (Component Object) stocker leurs données persistantes dans un seul fichier. Avec un stockage structuré, plusieurs composants logiciels différents peuvent partager un fichier de disque unique.  
  
 Vous avez plusieurs options en matière de persistance pour les éléments dans votre projet. Vous pouvez effectuer l’une des options suivantes :  
  
-   Enregistrez chaque fichier individuellement lorsqu’il a été modifié.  
  
-   Capturer le nombre de transactions dans un seul **enregistrer** opération.  
  
-   Enregistrer les fichiers localement, puis publier sur un serveur ou utiliser une autre approche de l’enregistrement d’éléments de projet lorsque l’élément représente une connexion de données à un objet distant.  
  
 Pour plus d’informations sur la persistance, consultez [persistance d’un projet](../../extensibility/internals/project-persistence.md) et [d’ouverture et de l’enregistrement des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="project-commitment-model"></a>Modèle de projet d’engagement  
 Objets de données persistantes ouvrira en mode direct ou en mode transactionnel ?  
  
 Lorsque des objets de données sont ouverts en mode direct, les modifications qui ont été apportées aux données sont incorporées immédiatement ou lorsque l’utilisateur enregistre manuellement le fichier.  
  
 Lorsque des objets de données sont ouverte à l’aide du mode de traitement, les modifications sont enregistrées dans un emplacement temporaire en mémoire et ne sont pas validées jusqu'à ce que l’utilisateur choisit manuellement enregistrer le fichier. À ce stade, toutes les modifications doivent se produire simultanément ou aucune modification ne sera apportée.  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Ouvrir et enregistrer des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Persistance d’un projet](../../extensibility/internals/project-persistence.md)   
 [Éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md)   
 [Composants de modèle de projet](../../extensibility/internals/project-model-core-components.md)   
 [Création de types de projets](../../extensibility/internals/creating-project-types.md)