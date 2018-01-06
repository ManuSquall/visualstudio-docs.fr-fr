---
redirect_url: shell/modifying-the-isolated-shell-by-using-the-dot-vsct-file
title: "Modification de l’interpréteur de commandes isolé à l’aide de le. Fichier VSCT | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ddf48e384b85946d4efcbb62359f24780507dfa4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Modification de l’interpréteur de commandes isolé à l’aide de le. Fichier VSCT
Le projet de l’interface utilisateur pour un projet de shell isolé Visual Studio contient un fichier .vsct qui vous permet de spécifier les groupes d’applications et les commandes individuelles sont disponibles dans l’application. Voici un extrait d’un fichier .vsct non modifié.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Par défaut, la plupart des commandes et des groupes de commandes sont inclus. Pour exclure une commande ou un groupe de commandes, il vous suffit ne commentez pas cette commande ou un groupe.  
  
 Par exemple, pour supprimer le volet suivant et les commandes de volet précédent, supprimez le `No_PaneNextPaneCommand` et `No_PanePrevPaneCommand` entrées :  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Pour plus détails exemple ces personnalisations, consultez [procédure pas à pas : création d’une Application de Shell isolé base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Fichiers référencés  
 Le fichier .vsct par défaut pour une application référence les fichiers suivants. Ces fichiers se trouvent dans le sous-répertoire \VisualStudioIntegration\Common\Inc\ du répertoire d’installation du SDK Visual Studio.  
  
|Fichier|Description|  
|----------|-----------------|  
|wbids.h|Identités de l’interface utilisateur pour le package Web Parcourir.|  
|AppIDCmdUsed.vsct|Table de commande pour les principaux éléments d’interface utilisateur de Visual Studio.|  
|EmulatorCmdUsed.vsct|Table de commande pour les éléments de l’interface utilisateur de l’émulation éditeur Emacs et résumé.|  
|Vsdebugguids.h|Définit les GUID des commandes, page options et autres fonctionnalités du débogueur Visual Studio.|  
|VsDbgCmdUsed.vsct|Table de commande pour le débogueur.|  
  
 Le fichier AppIDCmdUsed.vsct inclut des éléments de l’interface utilisateur de Visual Studio basés sur les symboles définis dans le fichier .vsct l’application.  
  
 Pour plus d’informations, consultez [conception d’une Table de commande XML (. Fichiers VSCT)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) et [référence du schéma XML de VSCT](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Shell isolé Visual Studio](../extensibility/visual-studio-isolated-shell.md)