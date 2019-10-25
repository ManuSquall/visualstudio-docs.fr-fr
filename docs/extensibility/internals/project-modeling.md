---
title: Modélisation de projet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42e810a36478e49a578c6713d20f1bfc6be98309
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725558"
---
# <a name="project-modeling"></a>Modélisation de projet
L’étape suivante de l’automatisation de votre projet consiste à implémenter les objets de projet standard : les collections <xref:EnvDTE.Projects> et `ProjectItems` ; objets `Project` et <xref:EnvDTE.ProjectItem> ; et les objets restants propres à votre implémentation. Ces objets standard sont définis dans le fichier Dteinternal. h. Une implémentation des objets standard est fournie dans l’exemple BscPrj. Vous pouvez utiliser ces classes en tant que modèles pour créer vos propres objets de projet standard qui résident côte à côte avec des objets de projet issus d’autres types de projets.

 Un consommateur Automation suppose pouvoir appeler <xref:EnvDTE.Solution> («`<UniqueProjName>")` et <xref:EnvDTE.ProjectItems> (`n`), où n est un numéro d’index pour obtenir un projet spécifique dans la solution. Si vous effectuez cet appel d’automatisation, l’environnement appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> sur la hiérarchie de projet appropriée, en transmettant VSITEMID_ROOT comme paramètre ItemID et VSHPROPID_ExtObject en tant que paramètre VSHPROPID. `IVsHierarchy::GetProperty` retourne un pointeur `IDispatch` vers l’objet Automation qui fournit l’interface `Project` principale, que vous avez implémentée.

 Voici la syntaxe de `IVsHierarchy::GetProperty`.

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

 L’imbrication signifie qu’un objet <xref:EnvDTE.ProjectItem> peut être <xref:EnvDTE.ProjectItems> collection en même temps, car une collection `ProjectItems` peut contenir les objets imbriqués. L’exemple de projet de base n’illustre pas cette imbrication. En implémentant l’objet `Project`, vous participez à la structure de type arborescence qui caractérise la conception du modèle Automation global.

 L’automatisation du projet suit le chemin d’accès dans le diagramme suivant.

 ![Objets de projet Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Automatisation de projet

 Si vous n’implémentez pas un objet `Project`, l’environnement renverra toujours un objet `Project` générique qui contient uniquement le nom du projet.

## <a name="see-also"></a>Voir aussi
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>