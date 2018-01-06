---
title: "Projet de modélisation | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 31c3d87a44838ead7663ff4c156985ab1b8e98eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="project-modeling"></a>Modélisation de projet
L’étape suivante dans grâce à l’automatisation de votre projet doit implémenter les objets du projet standard : le <xref:EnvDTE.Projects> et `ProjectItems` collections ; le `Project` et <xref:EnvDTE.ProjectItem> objets ; et les autres objets spécifiques à votre implémentation. Ces objets standards sont définis dans le fichier de Dteinternal.h. Une implémentation d’un des objets standards est fournie dans l’exemple BscPrj. Vous pouvez utiliser ces classes comme modèles pour créer votre propre projet standard des objets qui se trouvent côte à côte avec les objets du projet à partir d’autres types de projet.  
  
 Un consommateur automation suppose être en mesure d’appeler <xref:EnvDTE.Solution>(«`<UniqueProjName>")` et <xref:EnvDTE.ProjectItems> (`n`) où n est un numéro d’index pour l’obtention d’un projet spécifique dans la solution. Cet appel d’automation, l’environnement appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> sur la hiérarchie de projet approprié, en passant VSITEMID_ROOT comme paramètre de ItemID et VSHPROPID_ExtObject en tant que paramètre VSHPROPID. `IVsHierarchy::GetProperty`Retourne un `IDispatch` pointeur vers l’objet automation en fournissant le cœur `Project` interface, ce qui vous avez implémenté.  
  
 Voici la syntaxe de `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 Projets de prendre en charge l’imbrication et utilisent des collections pour créer des groupes d’éléments de projet. Voici à quoi ressemble la hiérarchie.  
  
```  
Projects  
  |- Project  
      |- ProjectItems (a collection of ProjectItem)  
          |- ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 Imbrication signifie qu’un <xref:EnvDTE.ProjectItem> objet peut être <xref:EnvDTE.ProjectItems> collection en même temps, car un `ProjectItems` collection peut contenir des objets imbriqués. L’exemple de projet de base ne présente pas cette imbrication. En implémentant le `Project` de l’objet, vous participez à la structure arborescente qui caractérise la conception de l’ensemble du modèle automation.  
  
 L’automatisation de projet suit le chemin d’accès dans le diagramme suivant.  
  
 ![Objets du projet Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Automation de projet  
  
 Si vous n’implémentez pas une `Project` de l’objet, l’environnement retourne toujours un type générique `Project` objet qui contient uniquement le nom du projet.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>