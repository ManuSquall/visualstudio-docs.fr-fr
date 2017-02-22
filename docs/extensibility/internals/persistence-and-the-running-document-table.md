---
title: "Persistance et la Table de Document en cours d&#39;ex&#233;cution | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "persistance, gestion"
  - "Interface IVsPersistHierarchyItem, l'implémentation"
  - "architecture de persistance"
  - "en cours d'exécution table document (r & DT), architecture"
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Persistance et la Table de Document en cours d&#39;ex&#233;cution
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dans la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, les projets sont entièrement responsables de la gestion de la persistance de leurs éléments de projet, ils accomplir à l'aide du service, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Les documents sont l'unité de base de la persistance dans l'environnement Visual Studio. Projets de coordonnent l'ouverture, l'enregistrement et changement de nom des documents avec la table document en cours d'exécution \(r & DT\), une ressource qui effectue le suivi de l'état de tous les documents ouverts.  
  
## Gestion de persistance  
 Projets de contrôle de service de persistance de l'environnement en implémentant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> interface. Bien que l'environnement demande jamais directement à un document vers persistant, il demande le projet propriétaire \(ou hiérarchie\) pour enregistrer le document. Cela rend possible pour le projet enregistrer ses données d'élément de projet dans les fichiers locaux, les fichiers à distance, une base de données, un référentiel ou un autre support.  
  
 L'environnement global conserve le r & DT. L'environnement comprend des entrées pour toutes les fenêtres ouvertes et de documents dans la r & DT, ce qui rend possible pour qu'ils puissent recevoir des notifications spéciales, telles que lors de la fermeture d'une solution. En outre, le r & DT rend possible pour l'environnement effectuer le suivi de leurs nœuds correspondants dans **l'Explorateur de solutions**. La r & DT conserve un enregistrement par objet persistant ouvert, y compris les fichiers projet et documents de l'élément de projet.  
  
## Voir aussi  
 [Table de Document en cours d’exécution](../../extensibility/internals/running-document-table.md)   
 [Sélection et la devise dans l’IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)