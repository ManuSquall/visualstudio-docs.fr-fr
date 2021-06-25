---
title: Persistance du projet | Microsoft Docs
description: En savoir plus sur la persistance dans la conception de votre projet, notamment l’utilisation de IPersistFileFormat pour conserver à la fois des objets de projet de fichier et non basés sur des fichiers.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 17b9fc40a93a926fde5edc28e93f7751b919611c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903643"
---
# <a name="project-persistence"></a>Persistance d’un projet
La persistance est un facteur clé de la conception de votre projet. La plupart des projets utilisent des éléments de projet qui représentent des fichiers ; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend également en charge les projets dont les données ne sont pas basées sur des fichiers. Les fichiers appartenant au projet et au fichier projet doivent être rendus persistants. L’IDE indique au projet de s’enregistrer lui-même ou un élément de projet.

 Les modèles pour les projets sont passés à la fabrique de projets. Les modèles doivent prendre en charge l’initialisation de tous les éléments de projet en fonction des spécifications du type de projet spécifique. Ces modèles peuvent être enregistrés plus tard en tant que fichiers projet et gérés par l’IDE par le biais de la solution. Pour plus d’informations, consultez [création d’instances de projet à l’aide de fabriques de projets](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) et de [solutions](../../extensibility/internals/solutions-overview.md).

 Les éléments de projet peuvent être basés sur des fichiers ou sur des fichiers non basés sur un fichier :

- Les éléments basés sur des fichiers peuvent être locaux ou distants. Dans les projets Web en C#, par exemple, les connexions aux fichiers sur un système distant sont conservées localement, tandis que les fichiers sont conservés sur le système distant.

- Les éléments non basés sur des fichiers peuvent enregistrer des éléments dans une base de données ou un référentiel.

## <a name="commit-models"></a>Valider les modèles
 Après avoir décidé de l’emplacement des éléments de projet, vous devez choisir le modèle de validation approprié. Par exemple, dans un modèle basé sur des fichiers avec des fichiers locaux, chaque projet peut être enregistré de manière autonome. Dans un modèle de référentiel, vous pouvez enregistrer plusieurs éléments dans une transaction. Pour plus d’informations, consultez [décisions de conception de type de projet](../../extensibility/internals/project-type-design-decisions.md).

 Pour déterminer les extensions de nom de fichier, les projets implémentent l' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interface, qui fournit des informations permettant au client d’un objet d’implémenter la boîte de dialogue **Enregistrer sous** , c’est-à-dire de remplir la liste déroulante **type** de fichier et de gérer l’extension de nom de fichier initiale.

 L’IDE appelle l' `IPersistFileFormat` interface sur le projet pour indiquer que le projet doit rendre ses éléments de projet persistants, le cas échéant. Par conséquent, l’objet possède tous les aspects de son fichier et de son format. Cela comprend le nom du format de l’objet.

 Dans le cas où les éléments ne sont pas des fichiers, `IPersistFileFormat` est toujours la manière dont les éléments non basés sur des fichiers sont conservés. Les fichiers projet, tels que les fichiers. vbp pour les [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projets ou les fichiers. vcproj pour les [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projets, doivent également être persistants.

 Pour les actions d’enregistrement, l’IDE examine la table de document en cours d’exécution (RDT) et la hiérarchie passe les commandes aux <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> interfaces et. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> méthode est implémentée pour déterminer si l’élément a été modifié. Si l’élément a la valeur, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> méthode est implémentée pour enregistrer l’élément modifié.

 Les méthodes de l' `IVsPersistHierarchyItem2` interface sont utilisées pour déterminer si un élément peut être rechargé et, si l’élément peut être, pour le recharger. En outre, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> méthode peut être implémentée pour entraîner la suppression des éléments modifiés sans enregistrement.

## <a name="see-also"></a>Voir aussi
- [Checklist : création de types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Création d’instances de projets à l’aide de fabriques de projets](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
