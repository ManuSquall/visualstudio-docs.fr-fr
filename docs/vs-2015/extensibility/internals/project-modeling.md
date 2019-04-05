---
title: Projet de modélisation | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e0edca4a45419a4a4c962ebf62b65e99c4732a12
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "58954194"
---
# <a name="project-modeling"></a>Modélisation de projet
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L’étape suivante de la fourniture de l’automatisation pour votre projet consiste à implémenter les objets de projet standard : le <xref:EnvDTE.Projects> et `ProjectItems` collections ; la `Project` et <xref:EnvDTE.ProjectItem> objets ; et les objets restants uniques à votre implémentation. Ces objets standards sont définis dans le fichier de Dteinternal.h. Une implémentation des objets standards est fournie dans l’exemple BscPrj. Vous pouvez utiliser ces classes en tant que modèles pour créer vos propres objets de projet standard qui en matière de côte à côte avec les objets du projet à partir d’autres types de projets.  
  
 Un utilisateur d’automation part du principe que pour être en mesure d’appeler <xref:EnvDTE.Solution>(«`<UniqueProjName>")` et <xref:EnvDTE.ProjectItems> (`n`) où n est un numéro d’index pour l’obtention d’un projet spécifique dans la solution. Cet appel d’automation, l’environnement d’appeler <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> sur la hiérarchie de projet approprié, en passant VSITEMID_ROOT comme paramètre d’ItemID et VSHPROPID_ExtObject en tant que paramètre VSHPROPID. `IVsHierarchy::GetProperty` Retourne un `IDispatch` pointeur vers l’objet automation fournir les principales `Project` interface, ce qui vous avez implémenté.  
  
 Voici la syntaxe de `IVsHierarchy::GetProperty`.  
  
 `HRESULT GetProperty (`  
  
 `VSITEMID` `itemid`,  
  
 `VSHPROPID` `propid`,  
  
 `VARIANT` `*pvar`  
  
 `);`  
  
 Projets de prendre en charge l’imbrication et utilisent des collections pour créer des groupes d’éléments de projet. La hiérarchie se présente comme suit.  
  
```  
Projects  
  |– Project  
      |– ProjectItems (a collection of ProjectItem)  
          |– ProjectItem (single object) or ProjectItems (another collection)  
```  
  
 L’imbrication signifie qu’un <xref:EnvDTE.ProjectItem> objet peut être <xref:EnvDTE.ProjectItems> collection en même temps, car un `ProjectItems` collection peut contenir des objets imbriqués. L’exemple de projet de base ne présente pas cette imbrication. En implémentant le `Project` de l’objet, vous participez à la structure arborescente qui caractérise la conception du modèle automation général.  
  
 L’automation de projet suit le chemin d’accès dans le diagramme suivant.  
  
 ![Objets du projet Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects")  
Automation de projet  
  
 Si vous n’implémentez pas un `Project` de l’objet, l’environnement retourne toujours un générique `Project` objet qui contient uniquement le nom du projet.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:EnvDTE.Projects>   
 <xref:EnvDTE.ProjectItem>   
 <xref:EnvDTE.ProjectItems>
