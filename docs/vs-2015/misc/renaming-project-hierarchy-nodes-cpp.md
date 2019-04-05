---
title: Renommer des nœuds de hiérarchie de projet (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- HierUtil7 sample [Visual Studio SDK], renaming project nodes
- project nodes, renaming in HierUtil7 sample
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: 7f6406936f293eea9c604b830f8eaab55a90a957
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "58949590"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>Changement de nom des nœuds de hiérarchie de projet (C++)
Vous pouvez renommer un nœud de hiérarchie de dossier de projet à l’aide de l’infrastructure de projet HierUtil7 pour C++ non managé. Pour plus d’informations, consultez [exemple HierUtil7](http://msdn.microsoft.com/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## <a name="expanding-the-hierarchy-node"></a>En développant le nœud de hiérarchie  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>Développez le nœud de hiérarchie et de renommer le dossier  
  
1.  Sélectionnez le nœud de hiérarchie à l’aide de la méthode suivante :  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` est le conteneur de la hiérarchie correspondant au dossier et `EXPF_SelectItem` provient le <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> énumération. Le `GUID_MacroExplorer` est une constante GUID définie dans Vsshell.idl et est un exemple de `rguidPersistenceSlot` dans la signature de fonction de `ExtExpand`, défini dans Hu_node.h.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Vous pouvez trouver le fichier Hu_node.h dans le dossier, \<racine d’installation > \Program Files\VSIP 8.0\EnvSDK\common\hierutil7 :  
  
2.  Renommez le dossier en publiant la commande de changement de nom à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` est un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> pointeur : `<IVsUIShell>``srpVsUIShell`. `guiVSStd97` est un identificateur unique du groupe de la commande à laquelle la commande `cmdidRename` appartient, défini dans Vsshlids.h.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de Types de projet](../extensibility/internals/creating-project-types.md)   
 [Exemples d’extensibilité Visual Studio](../misc/vssdk-samples.md)