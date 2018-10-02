---
title: Enregistrement d’un Document personnalisé | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5a25cc7f64c50ca088e11cc69a122f97333dfc3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504528"
---
# <a name="saving-a-custom-document"></a>Enregistrement d’un document personnalisé
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [enregistrer un Document de personnalisé](https://docs.microsoft.com/visualstudio/extensibility/internals/saving-a-custom-document).  
  
Les handles d’environnement le **enregistrer**, **enregistrer en tant que**, et **Enregistrer tout** commandes. Lorsqu’un utilisateur clique **enregistrer**, **enregistrer en tant que**, **ou enregistrer tout** sur le **fichier** menu ou ferme la solution, ce qui entraîne un Enregistrer tout, ce qui suit le processus se produit.  
  
 ![Enregistrer l’Éditeur du client](../../extensibility/internals/media/private.gif "privé")  
Enregistrer, enregistrer sous et enregistrer tout gestion des commandes pour un éditeur personnalisé  
  
 Ce processus est détaillé dans les étapes suivantes :  
  
1.  Pour le **enregistrer** et **enregistrer en tant que** des commandes, l’environnement utilise le <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> pour déterminer la fenêtre du document de service et par conséquent, les éléments qui doivent être enregistrés. Une fois que la fenêtre de document actif est connue, l’environnement recherche le pointeur de la hiérarchie et l’identificateur de l’élément (itemID) pour le document dans la table de document en cours d’exécution. Pour plus d’informations, consultez [Table de Document en cours d’exécution](../../extensibility/internals/running-document-table.md).  
  
     Pour la commande Enregistrer tout, l’environnement utilise les informations dans la table de document en cours d’exécution pour compiler la liste de tous les éléments à enregistrer.  
  
2.  Lorsque la solution reçoit un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> appel, il itère l’ensemble des éléments sélectionnés (autrement dit, les sélections multiples exposées par le <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service).  
  
3.  Sur chaque élément de la sélection, la solution utilise le pointeur de la hiérarchie pour appeler le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> méthode pour déterminer si la commande de menu Enregistrer doit être activée. Si un ou plusieurs éléments sont modifiés, la commande Enregistrer est activée. Si la hiérarchie utilise un éditeur standard, les délégués de hiérarchie recherchant dirty état à l’éditeur en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> (méthode).  
  
4.  Sur chaque élément sélectionné a été modifié, la solution utilise le pointeur de la hiérarchie pour appeler le <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> (méthode) sur les hiérarchies appropriés.  
  
     Dans le cas d’un éditeur personnalisé, la communication entre l’objet de données et le projet est privée. Par conséquent, les problèmes de persistance spéciaux sont gérées entre ces deux objets.  
  
    > [!NOTE]
    >  Si vous implémentez votre propre persistance, veillez à appeler la <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> méthode pour gagner du temps. Cette méthode vérifie qu’il est sûr enregistrer le fichier (par exemple, le fichier n’est pas en lecture seule).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Ouverture et enregistrement d’éléments de projet](../../extensibility/internals/opening-and-saving-project-items.md)

