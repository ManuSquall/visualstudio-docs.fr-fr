---
title: Modification du Shell isolé à l’aide de le. Fichier VSCT | Microsoft Docs
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952613"
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Modification du Shell isolé à l’aide de le. Fichier VSCT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le projet de l’interface utilisateur pour un projet de shell isolé Visual Studio contient un fichier .vsct qui vous permet de spécifier les groupes d’applications et les commandes individuelles sont disponibles dans l’application. Voici un extrait à partir d’un fichier .vsct non modifié.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Par défaut, la plupart des commandes et les groupes de commandes sont inclus. Pour exclure une commande ou un groupe de commandes, supprimez simplement cette commande ou ce groupe.  
  
 Par exemple, pour supprimer le volet suivant et les commandes de volet précédent, supprimez les commentaires de la `No_PaneNextPaneCommand` et `No_PanePrevPaneCommand` entrées :  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Pour une plus détaillée exemple ces personnalisations, consultez [procédure pas à pas : Création d’un base d’Application Shell isolée](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Fichiers référencés  
 Le fichier .vsct par défaut pour une application référence les fichiers suivants. Ces fichiers se trouvent dans le sous-répertoire \VisualStudioIntegration\Common\Inc\ du répertoire d’installation de Visual Studio SDK.  
  
|Fichier|Description|  
|----------|-----------------|  
|wbids.h|Identités de l’interface utilisateur pour le package Web Parcourir.|  
|AppIDCmdUsed.vsct|Table de commande pour les principaux éléments d’interface utilisateur de Visual Studio.|  
|EmulatorCmdUsed.vsct|Table de commande pour les éléments de l’interface utilisateur de l’émulation éditeur Emacs et en bref.|  
|Vsdebugguids.h|Définit les GUID des commandes, page options et autres fonctionnalités du débogueur Visual Studio.|  
|VsDbgCmdUsed.vsct|Table de commande pour le débogueur.|  
  
 Le fichier AppIDCmdUsed.vsct inclut des éléments de l’interface utilisateur de Visual Studio basés sur les symboles définis dans le fichier .vsct l’application.  
  
 Pour plus d’informations, consultez [conception XML Command Table (. Fichiers VSCT)](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) et [référence du schéma XML VSCT](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Shell isolé Visual Studio](../extensibility/visual-studio-isolated-shell.md)
