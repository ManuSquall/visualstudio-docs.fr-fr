---
title: Persistance de projet | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d77c307ec7b732ba727b7210b4f4eaacb44584aa
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="project-persistence"></a>Persistance d’un projet
La persistance est une considération de conception clés pour votre projet. La plupart des projets utilisent des éléments de projet qui représentent des fichiers ; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prend également en charge les projets dont les données sont non basée sur un fichier. Les deux fichiers détenus par le projet et le fichier projet doivent être persistante. L’IDE fait en sorte que le projet pour enregistrer lui-même ou un élément de projet.  
  
 Modèles de projets sont passés à la fabrique de projets. Les modèles doivent prendre en charge l’initialisation de tous les éléments de projet en fonction des spécifications du type de projet spécifique. Ces modèles ultérieurement peuvent être enregistrés en tant que fichiers de projet et gérés par l’IDE à la solution. Pour plus d’informations, consultez [création de projet d’Instances par à l’aide de projet fabriques](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) et [Solutions](../../extensibility/internals/solutions.md).  
  
 Éléments de projet peuvent être basée sur le fichier ou non basée sur un fichier :  
  
-   Éléments basés sur le fichier peuvent être local ou distant. Dans les projets Web en c#, par exemple, les connexions aux fichiers sur un système distant sont conservées localement, tandis que les fichiers eux-mêmes sont conservées sur le système distant.  
  
-   Éléments non basés sur des fichiers peuvent enregistrer des éléments dans une base de données ou le référentiel.  
  
## <a name="commit-models"></a>Validation des modèles  
 Après avoir décidé où se trouvent les éléments de projet, vous devez choisir le modèle de validation appropriées. Par exemple, dans un modèle basé sur le fichier avec les fichiers locaux, chaque projet peut être enregistré autonome. Dans un modèle de référentiel, vous pouvez enregistrer plusieurs éléments dans une transaction. Pour plus d’informations, consultez [décisions de conception de Type de projet](../../extensibility/internals/project-type-design-decisions.md).  
  
 Pour déterminer les extensions de nom de fichier, les projets d’implémentent le <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interface, qui fournit des informations permettant au client d’un objet d’implémenter le **Enregistrer sous** boîte de dialogue : autrement dit, pour remplir le **enregistrer en tant que Type**  déroulante Lister et gérer l’extension de nom de fichier initial.  
  
 Les appels de l’IDE le `IPersistFileFormat` selon le cas des éléments de l’interface sur le projet pour indiquer que le projet doit conserver son projet. Par conséquent, tous les aspects de son fichier et le format propriétaire de l’objet. Cela inclut le nom du format de l’objet.  
  
 Dans le cas où les éléments ne sont pas des fichiers, `IPersistFileFormat` est toujours en mode non fichier basé sur les éléments sont rendus persistants. Fichiers, tels que les fichiers .vbp pour projet [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] fichiers de projets ou .vcproj pour [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projets, doit également être persistante.  
  
 Pour enregistrer les actions, l’IDE examine la table de document en cours d’exécution (r & DT) et la hiérarchie passe les commandes à le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> interfaces. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> méthode est implémentée pour déterminer si l’élément a été modifié. Si l’élément a, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> méthode est implémentée pour enregistrer l’élément modifié.  
  
 Les méthodes sur le `IVsPersistHierarchyItem2` interface sont utilisées pour déterminer si un élément peut être rechargé et, si l’élément peut être, pour recharger. En outre, le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> méthode peut être implémentée pour les éléments modifiés être rejetés sans être enregistré.  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : Créer de nouveaux Types de projet](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Création d’instances de projets à l’aide de fabriques de projets](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)