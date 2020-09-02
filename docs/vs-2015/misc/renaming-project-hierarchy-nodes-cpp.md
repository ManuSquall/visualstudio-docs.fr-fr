---
title: Modification du nom des nœuds de hiérarchie de projet (C++) | Microsoft Docs
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
ms.openlocfilehash: c7ad43fe1fd0e22cd94194d3079761de812b6ced
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686586"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>Changement de nom des nœuds de hiérarchie de projet (C++)
Vous pouvez renommer un nœud de hiérarchie de dossiers de projet à l’aide de l’infrastructure de projet HierUtil7 pour le C++ non managé. Pour plus d’informations, consultez [exemple HierUtil7](https://msdn.microsoft.com/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## <a name="expanding-the-hierarchy-node"></a>Développement du nœud de la hiérarchie  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>Pour développer le nœud de la hiérarchie et renommer le dossier  
  
1. Sélectionnez le nœud de la hiérarchie à l’aide de la méthode suivante :  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` est le conteneur de hiérarchie correspondant au dossier et provient `EXPF_SelectItem` de l' <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> énumération. `GUID_MacroExplorer`Est une constante GUID définie dans vsshell. idl et est un exemple pour `rguidPersistenceSlot` dans la signature de fonction de `ExtExpand` , définie dans Hu_node. h.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Vous pouvez trouver le fichier Hu_node. h dans le dossier \<installation root> \Program Files\VSIP 8.0 \ EnvSDK\common\hierutil7 :  
  
2. Renommez le dossier en publiant la commande Rename à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` est un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> pointeur : `<IVsUIShell>``srpVsUIShell` . `guiVSStd97` identificateur unique du groupe de commandes auquel appartient la commande `cmdidRename` , défini dans Vsshlids. h.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de types de projets](../extensibility/internals/creating-project-types.md)   
 [Exemples d’extensibilité Visual Studio](../misc/vssdk-samples.md)