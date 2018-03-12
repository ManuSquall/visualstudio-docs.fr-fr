---
title: "Enregistrement d’un Document personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 2b19c6ba222644bc9d5fb97874f50bf6a6aa59d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="saving-a-custom-document"></a>Enregistrement d’un Document personnalisé
Les handles d’environnement la **enregistrer**, **enregistrer en tant que**, et **Enregistrer tout** commandes. Lorsqu’un utilisateur clique **enregistrer**, **enregistrer en tant que**, **ou enregistrer tout** sur la **fichier** menu ou de la fermeture de la solution, ce qui entraîne un Enregistrer tout, ce qui suit processus se produit.  
  
 ![Enregistrer l’Éditeur du client](../../extensibility/internals/media/private.gif "privé")  
Enregistrer, enregistrer sous, puis enregistrer tout gestion des commandes pour un éditeur personnalisé  
  
 Ce processus est détaillé dans les étapes suivantes :  
  
1.  Pour le **enregistrer** et **enregistrer en tant que** des commandes, l’environnement utilise le <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> pour déterminer la fenêtre du document de service et par conséquent, les éléments doivent être enregistrés. Une fois que la fenêtre de document actif est connue, l’environnement de recherche le pointeur de la hiérarchie et l’identificateur de l’élément (itemID) pour le document dans la table de document en cours d’exécution. Pour plus d’informations, consultez [Table de documents en cours d’exécution](../../extensibility/internals/running-document-table.md).  
  
     Pour la commande Enregistrer tout, l’environnement utilise les informations dans la table de document en cours d’exécution pour compiler la liste de tous les éléments à enregistrer.  
  
2.  Lorsque la solution reçoit un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> appel, il itère au sein du jeu d’éléments sélectionnés (autrement dit, les sélections multiples exposées par le <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service).  
  
3.  Sur chaque élément de la sélection, la solution utilise le pointeur de la hiérarchie pour appeler le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> méthode pour déterminer si la commande de menu Enregistrer doit être activée. Si un ou plusieurs éléments sont modifiés, la commande est activée. Si la hiérarchie utilise un éditeur standard, les délégués de la hiérarchie recherchant dirty état à l’éditeur en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> (méthode).  
  
4.  Sur chaque élément sélectionné n’est pas intègre, la solution utilise le pointeur de la hiérarchie pour appeler le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> méthode sur les hiérarchies appropriés.  
  
     Dans le cas d’un éditeur personnalisé, la communication entre l’objet de données du document et le projet est privée. Par conséquent, des problèmes de persistance spéciaux sont gérées entre ces deux objets.  
  
    > [!NOTE]
    >  Si vous implémentez votre propre persistance, veillez à appeler la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> méthode pour gagner du temps. Cette méthode vérifie pour vous assurer qu’il est sûr enregistrer le fichier (par exemple, le fichier n’est pas en lecture seule).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Ouverture et enregistrement d’éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)