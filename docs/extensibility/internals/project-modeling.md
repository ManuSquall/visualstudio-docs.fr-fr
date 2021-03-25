---
title: Modélisation de projet | Microsoft Docs
description: En savoir plus sur les objets de projet standard qui sont requis pour créer l’automatisation pour votre nouveau type de projet et le chemin d’accès que l’Automation de projet suit.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 506606291996c94ff10514c6c57f83c6e1133862
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105062822"
---
# <a name="project-modeling"></a>Modélisation de projet
L’étape suivante de l’automatisation de votre projet consiste à implémenter les objets de projet standard : les <xref:EnvDTE.Projects> `ProjectItems` collections et, les `Project` <xref:EnvDTE.ProjectItem> objets et et les objets restants propres à votre implémentation. Ces objets standard sont définis dans le fichier Dteinternal. h. Une implémentation des objets standard est fournie dans l’exemple BscPrj. Vous pouvez utiliser ces classes en tant que modèles pour créer vos propres objets de projet standard qui résident côte à côte avec des objets de projet issus d’autres types de projets.

 Un consommateur Automation suppose pouvoir appeler <xref:EnvDTE.Solution> (" `<UniqueProjName>")` et <xref:EnvDTE.ProjectItems> ( `n` ) où n est un numéro d’index pour obtenir un projet spécifique dans la solution. Si vous effectuez cet appel d’automatisation, l’environnement appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> sur la hiérarchie de projet appropriée, en passant VSITEMID_ROOT comme paramètre ItemId et VSHPROPID_ExtObject en tant que paramètre VSHPROPID. `IVsHierarchy::GetProperty` retourne un `IDispatch` pointeur vers l’objet Automation qui fournit l' `Project` interface principale, que vous avez implémentée.

 Voici la syntaxe de `IVsHierarchy::GetProperty` .

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Les projets prennent en charge l’imbrication et l’utilisation des collections pour créer des groupes d’éléments de projet. La hiérarchie ressemble à ce qui suit.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 L’imbrication signifie qu’un <xref:EnvDTE.ProjectItem> objet peut être <xref:EnvDTE.ProjectItems> collection en même temps, car une `ProjectItems` collection peut contenir des objets imbriqués. L’exemple de projet de base n’illustre pas cette imbrication. En implémentant l' `Project` objet, vous participez à la structure de type arborescence qui caractérise la conception du modèle Automation global.

 L’automatisation du projet suit le chemin d’accès dans le diagramme suivant.

 ![Objets de projet Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Automatisation de projet

 Si vous n’implémentez pas d' `Project` objet, l’environnement retourne toujours un `Project` objet générique qui contient uniquement le nom du projet.

## <a name="see-also"></a>Voir aussi
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
