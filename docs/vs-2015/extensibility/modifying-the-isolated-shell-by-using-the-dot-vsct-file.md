---
title: Modification de l’interpréteur de commandes isolé à l’aide de. Fichier vsct | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c106a04e809e772ac3b8a77192fb2f101161e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194231"
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Modification du shell isolé à l’aide du fichier .Vsct
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le projet d’interface utilisateur pour un projet Shell isolé Visual Studio contient un fichier. vsct qui vous permet de spécifier les groupes d’applications et les commandes individuelles disponibles dans l’application. Voici un extrait d’un fichier. vsct non modifié.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Par défaut, la plupart des commandes et des groupes de commandes sont inclus. Pour exclure une commande ou un groupe de commandes, supprimez simplement les marques de commentaire de cette commande ou de ce groupe.  
  
 Par exemple, pour supprimer le volet suivant et les commandes de volet précédentes, supprimez les marques de commentaire des `No_PaneNextPaneCommand` `No_PanePrevPaneCommand` entrées et :  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Pour obtenir un exemple plus détaillé de ces personnalisations, consultez [procédure pas à pas : création d’une application Shell isolée de base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Fichiers référencés  
 Le fichier default. vsct pour une application fait référence aux fichiers suivants. Ces fichiers se trouvent dans le sous-répertoire \VisualStudioIntegration\Common\Inc\ du répertoire d’installation du kit de développement logiciel (SDK) Visual Studio.  
  
|Fichier|Description|  
|----------|-----------------|  
|wbids. h|Identités de l’interface utilisateur pour le package de navigation Web.|  
|AppIDCmdUsed. vsct|Table de commandes pour les éléments principaux de l’interface utilisateur de Visual Studio.|  
|EmulatorCmdUsed. vsct|Table de commandes pour les éléments d’interface utilisateur d’émulation Emacs et Brief.|  
|Vsdebugguids. h|Définit les GUID des commandes, la page Options et d’autres fonctionnalités du débogueur Visual Studio.|  
|VsDbgCmdUsed. vsct|Table de commandes pour le débogueur.|  
  
 Le fichier AppIDCmdUsed. vsct contient des éléments d’interface utilisateur Visual Studio basés sur les symboles définis dans le fichier application. vsct.  
  
 Pour plus d’informations, consultez conception de la [table de commandes XML (. Vsct)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) et la [référence de schéma XML vsct](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Shell isolé Visual Studio](../extensibility/visual-studio-isolated-shell.md)
