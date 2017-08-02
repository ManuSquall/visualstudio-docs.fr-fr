---
title: "Mod&#233;lisation de projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Automation (Visual Studio SDK), l'implémentation des objets du projet"
  - "modèles de projet, automation"
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Mod&#233;lisation de projet
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'étape suivante en fournissant l'automation pour votre projet est d'implémenter les objets standard de projet : les collections d' <xref:EnvDTE.Projects> et d' `ProjectItems` ; les objets d' `Project` et d' <xref:EnvDTE.ProjectItem> ; et les objets restants uniques à votre implémentation.  Ces objets standard sont définis dans le fichier de Dteinternal.h.  Une implémentation des objets standard est fournie dans l'exemple de BscPrj.  Vous pouvez utiliser ces classes comme des modèles pour créer vos propres objets standard de projet qui se tiennent côte à côte avec les objets de projet de l'autre projet types.  
  
 un consommateur d'automation présume de pouvoir appeler <xref:EnvDTE.Solution> `` \("`<UniqueProjName>")` et <xref:EnvDTE.ProjectItems> \(`n`\) où n est un index pour obtenir un projet spécifique dans la solution.  Effectuer cet appel d'automation fait d'appeler l'environnement <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> sur la hiérarchie appropriée de projet, en passant VSITEMID\_ROOT comme paramètre d'ItemID et VSHPROPID\_ExtObject comme paramètre de VSHPROPID.  `IVsHierarchy::GetProperty` retourne un pointeur d' `IDispatch` à l'objet Automation fournissant une interface principale d' `Project` , que vous avez implémentée.  
  
 Voici la syntaxe d' `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 les projets s'adaptent à l'imbrication et les collections d'utilisation pour créer des groupes d'éléments de projet.  La hiérarchie se présente comme suit.  
  
```  
Projects  
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 L'imbrication signifie qu'un objet d' <xref:EnvDTE.ProjectItem> peut être collection d' <xref:EnvDTE.ProjectItems> en même temps car une collection d' `ProjectItems` peut contenir des objets imbriqués.  l'exemple de base de projet ne montre pas cette imbrication.  En implémentant l'objet d' `Project` , vous participent à la structure comme une arborescence qui caractérise la création du modèle Automation global.  
  
 l'automation de projet suit le chemin d'accès dans le diagramme suivant.  
  
 ![Objets de projet Visual Studio](~/extensibility/internals/media/projectobjects.gif "ProjectObjects")  
automation de projet  
  
 Si vous n'implémentez pas un objet d' `Project` , l'environnement retourne toujours un objet générique d' `Project` qui contient uniquement le nom du projet.  
  
## Voir aussi  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>