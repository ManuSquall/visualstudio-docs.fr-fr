---
title: "&#201;l&#233;ments d&#39;un mod&#232;le de projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "projets (Visual Studio SDK), mise en œuvre"
  - "modèles de projet"
  - "projets (Visual Studio SDK), éléments"
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# &#201;l&#233;ments d&#39;un mod&#232;le de projet
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les interfaces et les implémentations de tous les projets dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] partagent une structure de base : le modèle de projet pour votre type de projet.  Dans votre modèle de projet, qui est le VSPackage vous développez, vous créez des objets qui sont conformes à vos décisions de conception et travail avec la fonctionnalité globale fournie par l'IDE.  Même si vous permet de contrôler la manière dont un élément de projet est rendu persistant, par exemple, vous ne contrôlez pas de notification qu'un fichier doit être persistant.  Lorsqu'un utilisateur place le focus dans un élément de projet ouvert et choisit **Enregistrer** dans le menu de **Fichier** dans la barre de menus du [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , le code de votre type de projet doit arrêter la commande de l'IDE, rend le fichier, puis envoie la notification dans l'IDE que le fichier n'est plus modifié.  
  
 Votre VSPackage interagit avec l'IDE via les services qui fournissent l'accès aux interfaces de l'IDE.  Par exemple, via les services particuliers, vous surveillez et routez des commandes et indiquez les informations de contexte pour les sélections opérées dans le projet.  Toutes les fonctionnalités globale de l'IDE nécessaire pour votre VSPackage est fournie par les services.  Pour plus d'informations sur les services, consultez [Comment : obtenir un Service](../Topic/How%20to:%20Get%20a%20Service.md).  
  
 D'autres considérations relatives à l'implémentation :  
  
-   Un même modèle de projet peut contenir plusieurs types de projet.  
  
-   Le projet types et les fabriques propres du projet sont stockées indépendamment avec GUID.  
  
-   Chaque projet doit avoir un fichier modèle ou un Assistant pour initialiser le nouveau fichier projet lorsqu'un utilisateur crée un projet via [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface utilisateur.  Par exemple, les modèles de [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] initialisent ce qui passent par la suite les fichiers .vcproj.  
  
 L'illustration suivante montre les interfaces principales, les services, et les objets qui composent un mise en ? uvre de projet classique.  Vous pouvez utiliser le programme d'assistance d'application, HierUtil7, créer les objets sous\-jacents et d'autres zones fixes de programmation.  Pour plus d'informations sur le programme d'assistance de l'application HierUtil7, consultez l' [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/fr-fr/a5c16a09-94a2-46ef-87b5-35b815e2f346).  
  
 ![Graphique de modèle de projet Visual Studio](~/docs/extensibility/internals/media/vsprojectmodel.gif "vsProjectModel")  
modèle de projet  
  
 Pour plus d'informations sur les interfaces et les services répertoriés dans le diagramme précédent, et d'autres interfaces facultatives non inclus dans le diagramme, consultez [Composants de modèle de projet](../../extensibility/internals/project-model-core-components.md).  
  
 Les projets peuvent prendre en charge les commandes et doivent par conséquent implémenter l'interface de <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de participer aux commandes le routage via le contexte GUID de commande.  
  
## Voir aussi  
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/fr-fr/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [Composants de modèle de projet](../../extensibility/internals/project-model-core-components.md)   
 [Création d'Instances de projet à l'aide de fabriques de projet](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [Comment : obtenir un Service](../Topic/How%20to:%20Get%20a%20Service.md)   
 [Création de Types de projets](../../extensibility/internals/creating-project-types.md)