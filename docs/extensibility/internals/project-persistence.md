---
title: Persistance du projet (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10a9cde91c0181fbfefbaa353c7c3702f4b36819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706459"
---
# <a name="project-persistence"></a>Persistance d’un projet
La persistance est une considération de conception clé pour votre projet. La plupart des projets utilisent des éléments de projet qui représentent des fichiers; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend également en charge les projets dont les données ne sont pas basées sur les fichiers. Les dossiers appartenant au projet et le dossier du projet doivent être persistants. L’IDE demande au projet de se sauver ou d’un élément de projet.

 Les modèles de projets sont transmis à l’usine du projet. Les modèles doivent soutenir l’initialisation de tous les éléments du projet en fonction des exigences du type de projet spécifique. Ces modèles peuvent ensuite être enregistrés sous forme de fichiers de projet et gérés par l’IDE grâce à la solution. Pour plus d’informations, voir [Créer des instances de projet en utilisant des usines](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) et des solutions [de](../../extensibility/internals/solutions-overview.md)projet .

 Les éléments du projet peuvent être basés sur des fichiers ou non :

- Les éléments basés sur les fichiers peuvent être locaux ou éloignés. Dans les projets Web en C, par exemple, les connexions aux fichiers d’un système distant persistent localement, tandis que les fichiers eux-mêmes persistent sur le système distant.

- Les éléments non basés sur les fichiers peuvent enregistrer des éléments dans une base de données ou un référentiel.

## <a name="commit-models"></a>Modèles d’engagement
 Après avoir décidé où se trouvent les éléments du projet, vous devez choisir le modèle de validation approprié. Par exemple, dans un modèle basé sur des fichiers avec des fichiers locaux, chaque projet peut être enregistré de manière autonome. Dans un modèle de référentiel, vous pouvez enregistrer plusieurs éléments en une seule transaction. Pour plus d’informations, voir [Project Type Design Decisions](../../extensibility/internals/project-type-design-decisions.md).

 Pour déterminer les extensions de <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> nom de fichier, les projets implémentent l’interface, qui fournit des informations permettant au client d’un objet de mettre en œuvre la boîte de dialogue **Save As,** c’est-à-dire de remplir la liste **d’abandon de Save As Type** et de gérer l’extension initiale du nom de fichier.

 L’IDE `IPersistFileFormat` appelle l’interface sur le projet pour indiquer que le projet doit persister ses éléments de projet le cas échéant. Par conséquent, l’objet possède tous les aspects de son fichier et de son format. Cela inclut le nom du format de l’objet.

 Dans le cas où `IPersistFileFormat` les éléments ne sont pas des fichiers, est toujours la façon dont les éléments non-fichier-basé sont persistés. Les fichiers de projet, tels [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] que les fichiers .vbp pour les projets ou les fichiers .vcproj pour [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] les projets, doivent également être persistants.

 Pour enregistrer les actions, l’IDE examine la table de document en <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> cours <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> d’exécution (RDT) et la hiérarchie passe les commandes aux interfaces et aux interfaces. La <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> méthode est mise en œuvre pour déterminer si l’élément a été modifié. Si l’élément <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> l’a fait, la méthode est implémentée pour enregistrer l’élément modifié.

 Les méthodes `IVsPersistHierarchyItem2` de l’interface sont utilisées pour déterminer si un élément peut être rechargé et, si l’élément peut l’être, pour le recharger. En outre, la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> méthode peut être implémentée pour faire en sorte que les éléments modifiés soient jetés sans être enregistrés.

## <a name="see-also"></a>Voir aussi
- [Liste de vérification : création de nouveaux types de projets](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Création d’instances de projets à l’aide de fabriques de projets](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
