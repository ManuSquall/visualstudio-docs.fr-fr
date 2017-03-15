---
title: "D&#233;cisions de conception de Type de projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "types de projets, persistance d'un fichier projet"
  - "types de projets, les mécanismes d'engagement"
  - "types de projets, des éléments"
  - "types de projets, les décisions de conception"
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# D&#233;cisions de conception de Type de projet
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Avant de créer un nouveau type de projet, vous devez prendre plusieurs décisions de conception concernant votre type de projet.  Vous devez choisir les types d'éléments vos projets intègrent, comment les fichiers projet sont rendus persistants, et les modèle d'engagement vous utiliserez.  
  
## éléments de projet  
 votre projet utilisera\-il des fichiers ou des objets abstraits ?  si vous utilisez des fichiers, référence\-seront\-ils basés ou les fichiers basés sur des répertoires ?  les fichiers ou les objets abstraits vont\-ils être locaux ou distants ?  
  
 Les éléments d'un projet peuvent être des fichiers, ou peuvent être des objets plus abstraits tels que des objets dans une base de données de référentiel ou des connexions de données via Internet.  Si les éléments sont des fichiers, le projet peut être un projet référence\-basé ou basée sur des répertoires.  
  
 Dans les projets fondés sur, les éléments peuvent apparaître dans plusieurs projets.  Toutefois, le fichier réel qu'un élément représente est situé dans un répertoire uniquement.  Dans les projets basés sur des répertoires, tous les éléments de projet existent dans la structure de répertoires.  Pour plus d'informations, consultez [NIB:Item Management in Projects](http://msdn.microsoft.com/fr-fr/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 Les éléments locaux sont stockés sur le même ordinateur où l'application.  Les éléments distants peuvent être stockés sur un serveur distinct dans un réseau local, ou ailleurs sur Internet.  
  
## persistance de fichier projet  
 Est\-ce\-que les données seront enregistrées dans les systèmes de fichiers plat communs, ou dans le stockage structuré ?  Est\-ce\-que les fichiers seront ouverts à l'aide d'un éditeur standard, ou d'un éditeur spécifique au projet ?  
  
 Pour rendre leurs données, la plupart des applications enregistrent leurs données dans un fichier, puis y lire en arrière lorsqu'un utilisateur doit examiner ou modifier les informations.  
  
 Le stockage structuré, également appelés fichiers composés, est couramment utilisé lorsque plusieurs objets \(COM\) de modèle COM doivent enregistrer leurs données persistantes dans un fichier unique.  Grâce à le stockage structuré, plusieurs composants logiciels peuvent partager un fichier sur disque unique.  
  
 Vous disposez de plusieurs options d'envisager de considérer la persistance des éléments contenus dans votre projet.  Vous pouvez effectuer l'une des options suivantes :  
  
-   Enregistrez chaque fichier individuellement lorsqu'il a été modifié.  
  
-   Capturez plusieurs transactions dans une seule opération d' **Enregistrer** .  
  
-   Enregistrez les fichiers localement, puis publier sur un serveur ou utilisent une autre approche pour stocker des éléments de projet lorsque l'élément représente une connexion de données à un objet distant.  
  
 Pour plus d'informations sur la persistance, consultez [Persistance d'un projet](../../extensibility/internals/project-persistence.md) et l' [Ouvrir et enregistrer des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## Modèle de l'engagement de projet  
 Est\-ce\-que les objets de données persistantes seront ouverts en mode direct ou le mode traité ?  
  
 Lorsque les objets de données sont ouverts en mode direct, les modifications apportées aux données sont incorporées immédiatement ou lorsque l'utilisateur enregistre manuellement le fichier.  
  
 Lorsque les objets de données sont ouverts à l'aide de le mode traité, les modifications sont stockés dans un emplacement temporaire de la mémoire et ne sont pas validés tant que l'utilisateur a choisi manuellement pour enregistrer le fichier.  à ce moment\-là, toutes les modifications doivent se produire ensemble ou aucune modification ne sera apportée.  
  
## Voir aussi  
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [NIB:Item Management in Projects](http://msdn.microsoft.com/fr-fr/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [Ouvrir et enregistrer des éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Persistance d'un projet](../../extensibility/internals/project-persistence.md)   
 [Éléments d'un modèle de projet](../../extensibility/internals/elements-of-a-project-model.md)   
 [Composants de modèle de projet](../../extensibility/internals/project-model-core-components.md)   
 [Création de Types de projets](../../extensibility/internals/creating-project-types.md)