---
title: "Changement de nom des nœuds de hi&#233;rarchie de projet (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Exemple HierUtil7 (Kit de développement logiciel Visual Studio ), changement de nom des nœuds de projet"
  - "nœuds de projet, changement de nom dans l’exemple HierUtil7"
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
caps.handback.revision: 12
manager: "douge"
---
# Changement de nom des nœuds de hi&#233;rarchie de projet (C++)
Vous pouvez renommer un nœud de la hiérarchie du dossier du projet à l'aide de l'infrastructure du projet HierUtil7 pour le code C\+\+ non managé.  Pour plus d'informations, consultez [HierUtil7 Sample](http://msdn.microsoft.com/fr-fr/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## Développez le nœud de la hiérarchie  
  
#### Pour développer le nœud de la hiérarchie et renommer le dossier  
  
1.  Sélectionnez le nœud de la hiérarchie à l'aide de la méthode suivante :  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` est le conteneur de hiérarchie correspondant au dossier et `EXPF_SelectItem` est de l'énumération d' <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> .  `GUID_MacroExplorer` est une constante GUID définie dans Vsshell.idl et est un exemple d' `rguidPersistenceSlot` dans la signature de la fonction d' `ExtExpand`, définie dans Hu\_node.h.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Vous pouvez rechercher le fichier dans le dossier de Hu\_node.h, \<installation root\> \\Program Files\\VSIP 8.0\\EnvSDK \\ common \\ merge hierutil7 :  
  
2.  Renommez le dossier en émettant la commande renommer à l'aide de l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` est un pointeur d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> : `<IVsUIShell>``srpVsUIShell`.  `guiVSStd97` est un identificateur unique du groupe de commandes auquel la commande `cmdidRename` appartient, défini dans Vsshlids.h.  
  
## Voir aussi  
 [Création de Types de projets](../extensibility/internals/creating-project-types.md)   
 [Exemples d’extensibilité Visual Studio](../misc/vssdk-samples.md)