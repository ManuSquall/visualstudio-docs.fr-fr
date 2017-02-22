---
title: "Persistance d&#39;un projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "persistance, projets"
  - "persistance de projets (Visual Studio SDK),"
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Persistance d&#39;un projet
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La persistance est une considération principale de conception pour votre projet.  La plupart des éléments de projet à utiliser des projets qui représentent les fichiers ; de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projets en charge également des données non\-fichier\-est via.  Les deux fichiers appartenant à le projet et le fichier projet doivent être persistants.  L'IDE indique au projet de l'enregistrement ou un élément de projet.  
  
 Les modèles de projets sont passés à la fabrique de projet.  Les modèles doivent prendre en charge l'initialisation de tous les éléments de projet en fonction de les spécifications du type de projet spécifique.  Ces modèles peuvent ensuite être enregistrés en tant que fichiers projet et être gérés par l'IDE via la solution.  Pour plus d'informations, consultez [Création d'Instances de projet à l'aide de fabriques de projet](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) et [Solutions](../../extensibility/internals/solutions.md).  
  
 les éléments de projet peuvent être basés sur des fichiers ou non\-fichier\-basés :  
  
-   les articles de base peuvent être locaux ou distants.  Dans les projets Web en c\#, par exemple, les connexions aux fichiers sur un système distant sont persistantes localement, bien que les fichiers eux\-mêmes sont persistantes sur le système distant.  
  
-   les éléments Non\-fichier\-basés peuvent enregistrer des éléments à une base de données ou à une base de données de référentiel.  
  
## modèles de validation  
 après avoir décidé où les éléments de projet sont localisés, vous devez choisir le modèle approprié de validation.  Par exemple, dans un modèle basé sur des fichiers avec des fichiers locaux, chaque projet peut être stocké autonome.  Dans un modèle de base de données de référentiel, vous pouvez enregistrer plusieurs éléments dans une transaction.  Pour plus d'informations, consultez [Décisions de conception de Type de projet](../../extensibility/internals/project-type-design-decisions.md).  
  
 Pour déterminer des extensions de nom de fichier, les projets implémentent l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> , qui fournit des informations permettant au client d'un objet pour implémenter la boîte de dialogue d' **Enregistrer sous** zone\-qu'est, pour effectuer la liste déroulante de **Type de fichier** et pour gérer l'extension de nom de fichier d'origine.  
  
 L'IDE appelle l'interface d' `IPersistFileFormat` sur le projet pour indiquer que le projet doit rendre ses éléments de projet appropriés.  par conséquent, l'objet possède tous les aspects de son fichier et format.  Cela inclut le nom du format de l'objet.  
  
 Dans le cas où les éléments ne sont pas des fichiers, `IPersistFileFormat` est toujours comment les éléments non\-fichier\-basés sont rendus persistants.  Les fichiers projet, tels que les fichiers de .vbp pour les projets de [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] ou des fichiers .vcproj pour les projets de [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] , doivent également être persistants.  
  
 Pour les actions de sauvegarde, l'IDE examine le tableau en cours de exécution de \(RDT\) document et la hiérarchie passe les commandes à <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> et les interfaces d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> .  la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> est implémentée pour déterminer si l'élément a été modifié.  Si l'élément a, la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> est implémentée pour enregistrer l'élément modifié.  
  
 Les méthodes de l'interface d' `IVsPersistHierarchyItem2` sont utilisées pour déterminer si un élément peut être rechargé et, si l'élément peut être, pour le recharger.  En outre, la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> peut être implémentée pour que les éléments modifiés à ignorer sans être enregistré.  
  
## Voir aussi  
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Création d'Instances de projet à l'aide de fabriques de projet](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)