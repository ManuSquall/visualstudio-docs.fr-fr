---
title: Modélisation du projet (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1ac89baf5bc7582d3430532938a5e5a0c35a4c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706556"
---
# <a name="project-modeling"></a>Modélisation de projet
La prochaine étape dans la fourniture d’automatisation pour <xref:EnvDTE.Projects> votre `ProjectItems` projet est de mettre en œuvre les objets de projet standard: le et les collections; les `Project` <xref:EnvDTE.ProjectItem> objets et les objets; et les objets restants propres à votre implémentation. Ces objets standard sont définis dans le fichier Dteinternal.h. Une mise en œuvre des objets standard est fournie dans l’échantillon BscPrj. Vous pouvez utiliser ces classes comme modèles pour créer vos propres objets de projet standard qui se dressent côte à côte avec des objets de projet d’autres types de projets.

 Un consommateur d’automatisation suppose <xref:EnvDTE.Solution>être`<UniqueProjName>")` en <xref:EnvDTE.ProjectItems> `n`mesure d’appeler (" et ) où n est un numéro d’index pour l’obtention d’un projet spécifique dans la solution. Cet appel d’automatisation amène <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> l’environnement à faire appel à la hiérarchie de projet appropriée, en passant VSITEMID_ROOT comme paramètre ItemID et VSHPROPID_ExtObject comme paramètre VSHPROPID. `IVsHierarchy::GetProperty`retourne `IDispatch` un pointeur à l’objet d’automatisation fournissant l’interface de base, `Project` que vous avez implémentée.

 Ce qui suit est `IVsHierarchy::GetProperty`la syntaxe de .

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Les projets accueillent la nidification et utilisent des collections pour créer des groupes d’éléments du projet. La hiérarchie ressemble à ceci.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 La nidification <xref:EnvDTE.ProjectItem> signifie qu’un objet peut <xref:EnvDTE.ProjectItems> `ProjectItems` être collectionné en même temps parce qu’une collection peut contenir les objets imbriqués. L’échantillon du projet de base ne démontre pas cette nidification. En implémentant l’objet, `Project` vous participez à la structure en nature d’arbre qui caractérise la conception du modèle d’automatisation global.

 L’automatisation du projet suit le chemin dans le diagramme suivant.

 ![Objets visual studio project](../../extensibility/internals/media/projectobjects.gif "ProjetObjects") Automatisation du projet

 Si vous n’implémentez pas un `Project` `Project` objet, l’environnement retournera toujours un objet générique qui ne contient que le nom du projet.

## <a name="see-also"></a>Voir aussi
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
