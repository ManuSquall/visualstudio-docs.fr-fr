---
title: Persistance et la table de documents en cours d’exécution | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2c422ad1735312c82c8dc027c4adf73c1b033685
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196095"
---
# <a name="persistence-and-the-running-document-table"></a>Persistance et table de document en cours d’exécution
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dans l' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE, les projets sont entièrement responsables de la gestion de la persistance de leurs éléments de projet, qu’ils effectuent à l’aide du service, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . Les documents sont l’unité de persistance de base dans l’environnement Visual Studio. Les projets coordonnent l’ouverture, l’enregistrement et le changement de nom des documents avec la table de documents en cours d’exécution (RDT), une ressource qui suit l’état de tous les documents ouverts.  
  
## <a name="managing-persistence"></a>Gestion de la persistance  
 Les projets contrôlent le service de persistance de l’environnement en implémentant l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interface. Alors que l’environnement ne demande jamais directement à un document de persister, il demande au projet propriétaire (ou à la hiérarchie) d’enregistrer le document. Cela permet au projet d’enregistrer ses données d’élément de projet dans des fichiers locaux, des fichiers distants, une base de données, un référentiel ou un autre support.  
  
 L’environnement global gère le RDT. L’environnement contient des entrées pour toutes les fenêtres et tous les documents ouverts dans RDT, ce qui leur permet de recevoir des notifications spéciales, par exemple quand une solution est fermée. En outre, l’RDT permet à l’environnement de suivre les nœuds correspondants dans **Explorateur de solutions**. Le RDT gère un enregistrement par objet persistant ouvert, y compris les fichiers projet et les documents d’élément de projet.  
  
## <a name="see-also"></a>Voir aussi  
 [Table de document en cours d’exécution](../../extensibility/internals/running-document-table.md)   
 [Sélection et devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
