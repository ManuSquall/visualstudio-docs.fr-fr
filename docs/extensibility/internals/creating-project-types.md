---
title: "Cr&#233;ation de Types de projets | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "types de projets, nouveau"
  - "types de projets (Visual Studio SDK), nouveau projet"
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Cr&#233;ation de Types de projets
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Vous pouvez étendre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en créant un nouveau type de projet. Pour créer un nouveau type de projet, vous devez comprendre les différents concepts et effectuer un certain nombre d’étapes. Les rubriques suivantes fournissent une vue d’ensemble de la création de types de projets.  
  
## Dans cette section  
 [Décisions de conception de Type de projet](../../extensibility/internals/project-type-design-decisions.md)  
 Décrit l’article, persistance d’un fichier projet et les décisions de conception mécanique engagement que vous devez effectuer avant de créer un nouveau type de projet.  
  
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Fournit une vue d’ensemble des étapes à suivre pour créer un nouveau type de projet qui prend en charge les tâches de programmation en tant que la modification de code et compiler, création, le débogage et déploiement d’applications dans votre projet.  
  
 [Création d'Instances de projet à l'aide de fabriques de projet](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Fournit des informations sur la façon de fournir et d’utiliser une fabrique de projet pour créer des instances d’un nouveau projet.  
  
 [L'inscription d'un Type de projet](../../extensibility/internals/registering-a-project-type.md)  
 Fournit des exemples de code d’instructions à partir du Registre qui fournissent des chemins d’accès par défaut et des données et une table qui contient des entrées à partir du script de Registre pour chaque instruction.  
  
 [Persistance d'un projet](../../extensibility/internals/project-persistence.md)  
 Décrit l’utilisation de `IPersistFileFormat` pour conserver les objets fichier et non basés sur un fichier de projet.  
  
 [À l’aide de MSBuild](../../extensibility/internals/using-msbuild.md)  
 Décrit comment votre type de projet peut utiliser le [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] moteur pour permettre aux utilisateurs de construire à partir de génération [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dans la ligne de commande.  
  
## Rubriques connexes  
 [Prise en charge d'outils de consultation du symbole](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Décrit l’architecture de code des outils d’affichage tels que les **Explorateur d’objets** et **affichage de classes** fenêtre. Décrit les interfaces et les méthodes qui sont utilisées pour implémenter l’exploration des objets dans un VSPackage.  
  
 [Ajout de projet et modèles d'élément de projet](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Explique l’importance que les projets jouent dans la détermination de l’éditeur est utilisé lorsqu’un élément de projet est ouvert et comment les ressources de projet peuvent être manipulées.  
  
 [Installation de packages VS avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Montre comment permettre à votre VSPackage sa propre identité unique et comment encapsuler vos DLL VSPackage et autres informations dans un package Windows Installer \(. Fichier MSI\) pour le déploiement de vos clients.  
  
 [Hiérarchies dans Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Décrit comment [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] les vues et les adresses des hiérarchies.  
  
 [Packages VS](../../extensibility/internals/vspackages.md)  
 Fournit une vue d’ensemble d’un VSPackage, un objet COM pouvant être installé qui étend la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement et explique comment implémenter votre propre VSPackage.  
  
 [Types de projet](../../extensibility/internals/project-types.md)  
 Explique comment utiliser des projets pour modifier le code, compiler et générer du code, exécuter et déboguer du code et fournit des liens vers des rubriques détaillées sur la création de types de projets.