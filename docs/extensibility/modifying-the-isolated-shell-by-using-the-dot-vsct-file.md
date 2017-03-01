---
title: "Modification de l’interpréteur de commandes isolé à l’aide de la. Fichier VSCT | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: a20b546c6e8d6d70a17d3d0bae575a5b2898d781
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Modification de l’interpréteur de commandes isolé à l’aide de la. Fichier VSCT
Le projet de l’interface utilisateur pour un projet de shell isolé Visual Studio contient un fichier .vsct qui vous permet de spécifier les groupes d’applications et les commandes individuelles sont disponibles dans l’application. Voici un extrait d’un fichier .vsct non modifié.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Par défaut, la plupart des commandes et des groupes de commandes sont inclus. Pour exclure une commande ou un groupe de commandes, supprimez simplement cette commande ou ce groupe.  
  
 Par exemple, pour supprimer les commandes de volet précédent Volet suivant, supprimez le `No_PaneNextPaneCommand` et `No_PanePrevPaneCommand` entrées :  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Pour plus de détails exemple ces personnalisations, consultez [procédure pas à pas : création d’une Application de Shell isolé base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Fichiers référencés  
 Le fichier .vsct par défaut pour une application référence les fichiers suivants. Ces fichiers se trouvent dans le sous-répertoire \VisualStudioIntegration\Common\Inc\ du répertoire d’installation Visual Studio SDK.  
  
|Fichier|Description|  
|----------|-----------------|  
|wbids.h|Identités de l’interface utilisateur pour le package Web Parcourir.|  
|AppIDCmdUsed.vsct|Tableau de commandes pour les principaux éléments d’interface utilisateur de Visual Studio.|  
|EmulatorCmdUsed.vsct|Tableau de commandes pour les éléments de l’interface utilisateur de l’émulation éditeur Emacs et Brief.|  
|Vsdebugguids.h|Définit les GUID des commandes, page options et autres fonctionnalités du débogueur Visual Studio.|  
|VsDbgCmdUsed.vsct|Table de commande pour le débogueur.|  
  
 Le fichier AppIDCmdUsed.vsct inclut des éléments de l’interface utilisateur de Visual Studio basés sur les symboles définis dans le fichier .vsct l’application.  
  
 Pour plus d’informations, consultez [conception d’une Table de commande XML (. Les fichiers VSCT)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) et [référence de schéma XML de VSCT](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Isolé du Shell Visual Studio](../extensibility/visual-studio-isolated-shell.md)
