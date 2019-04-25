---
title: Les décisions de conception de Type de projet | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 323fbbc48953537dbcad4a13d2774fefec65dd52
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952562"
---
# <a name="project-type-design-decisions"></a>Décisions de conception de type de projet
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Avant de créer un nouveau type de projet, vous devez prendre des décisions de conception plusieurs concernant votre type de projet. Vous devez décider quels types d’éléments que contient vos projets, mode de conservation des fichiers projet et quel modèle d’engagement que vous allez utiliser.  
  
## <a name="project-items"></a>Éléments de projet  
 Votre projet utilise les fichiers ou des objets abstraits ? Si vous utilisez des fichiers, ils seront fichiers basée sur le répertoire ou référence ? Sont des fichiers ou des objets abstraits doivent passer soit local ou distant ?  
  
 Les éléments dans un projet peuvent être des fichiers, ou ils peuvent être des objets plus abstraits tels que les objets dans un référentiel ou des données des connexions de base de données sur Internet. Si les éléments sont des fichiers, le projet peut être basée sur une référence ou un projet basé sur le répertoire.  
  
 Dans les projets de base de référence, les éléments peuvent apparaître dans plusieurs projets. Toutefois, le fichier réel qui représente un élément se trouve dans un répertoire uniquement. Dans les projets basée sur le répertoire, tous les éléments de projet existent dans la structure de répertoires. Pour plus d’informations, consultez [NIB : gestion des éléments dans les projets](http://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 Les éléments locaux sont stockés sur le même ordinateur où l’application est installée. Les éléments à distance peuvent être stockées sur un serveur distinct dans un réseau local, ou un autre emplacement sur Internet.  
  
## <a name="project-file-persistence"></a>Persistance d’un fichier projet  
 Données seront-elles stockées dans les systèmes de fichiers plats courants, ou dans un stockage structuré ? Fichiers ouvrir à l’aide d’un éditeur standard ou un éditeur spécifique au projet ?  
  
 Pour conserver leurs données, la plupart des applications enregistrent leurs données dans un fichier et lisez-le lorsqu’un utilisateur doit vérifier ou modifier les informations.  
  
 Un stockage structuré, également appelé fichiers composés, est généralement utilisé lorsque vous avez besoin de plusieurs objets de composant COM (Object Model) stocker leurs données persistantes dans un seul fichier. Avec un stockage structuré, plusieurs différents composants logiciels peuvent partager un seul fichier de disque.  
  
 Vous avez plusieurs options en matière de persistance pour les éléments dans votre projet. Vous pouvez effectuer l’une des options suivantes :  
  
- Enregistrez chaque fichier individuellement lorsqu’il a été modifié.  
  
- Capturer le nombre de transactions dans un seul **enregistrer** opération.  
  
- Enregistrer les fichiers localement, puis publier sur un serveur ou utiliser une autre approche pour l’enregistrement des éléments de projet lorsque l’élément représente une connexion de données à un objet distant.  
  
  Pour plus d’informations sur la persistance, consultez [persistance d’un projet](../../extensibility/internals/project-persistence.md) et [d’ouverture et de l’enregistrement des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="project-commitment-model"></a>Modèle de projet d’engagement  
 Objets de données persistantes ouvrira en mode direct ou en mode transactionnel ?  
  
 Lorsque les objets de données sont ouverts en mode direct, les modifications qui ont été apportées aux données sont incorporées immédiatement ou lorsque l’utilisateur enregistre manuellement le fichier.  
  
 Lorsque les objets de données sont ouverts à l’aide du mode traité, les modifications sont enregistrées dans un emplacement temporaire en mémoire et ne sont pas validées jusqu'à ce que l’utilisateur choisit manuellement enregistrer le fichier. À ce stade, toutes les modifications doivent se produire ensemble ou aucune modification ne sera apportée.  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [NIB : gestion des éléments dans les projets](http://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [Ouvrir et enregistrer des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Persistance d’un projet](../../extensibility/internals/project-persistence.md)   
 [Éléments d’un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md)   
 [Composants principaux du modèle projet](../../extensibility/internals/project-model-core-components.md)   
 [Création de types de projets](../../extensibility/internals/creating-project-types.md)
