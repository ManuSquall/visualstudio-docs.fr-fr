---
title: Prise en charge de la persistance de l’État | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state persistence, managed package framework support
- managed package framework, state persistence support
- state, persistence
ms.assetid: d25866f2-8d1f-477f-8aa5-3af3fbbf6e97
caps.latest.revision: 15
manager: jillfra
ms.openlocfilehash: 6dc542d2e410b79a21e436a1881c06bd3cc4eef8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434317"
---
# <a name="support-for-state-persistence"></a>Prise en charge de la persistance de l’état
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] peut conserver l’état des objets communs. Par exemple, les propriétés de la solution et du projet sont enregistrées et restaurées dans les fichiers solution et projet. Les paramètres utilisateur peuvent être exportés et importés à partir des fichiers de paramètres.  
  
 Les VSPackages s’appuient généralement sur le stockage local, soit dans le registre système, soit dans le dossier Application Data pour l’utilisateur ou l’ordinateur actuel. Les valeurs qui requièrent une petite quantité d’espace pour le stockage, telles que les entiers et les chaînes, sont généralement stockées dans le registre système. Les valeurs qui requièrent beaucoup d’espace pour le stockage, telles que les bitmaps, sont enregistrées dans un fichier. Le chemin d’accès du fichier peut lui-même être enregistré dans le registre système. Le mécanisme de persistance doit avoir l’autorisation d’accéder au stockage local.  
  
## <a name="support-for-locating-local-storage"></a>Prise en charge de la localisation du stockage local  
 La <xref:Microsoft.VisualStudio.Shell.Package> classe fournit la prise en charge de la localisation des informations d’État dans le dossier du Registre système ou des données d’application pour l’utilisateur ou l’ordinateur actuel.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 Retourne le chemin d’accès de la racine de registre de l’ordinateur local pour [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , par exemple, HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0exp.  
  
 La racine du registre local est obtenue à partir du <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> service. Si ce n’est pas possible, il est obtenu à partir de l' <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> attribut du VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 Retourne le chemin d’accès de la racine de Registre (par ordinateur) de l’utilisateur actuel pour [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , par exemple, HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0exp.  
  
 La racine du registre local est obtenue à partir du <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> service. Si ce n’est pas possible, il est obtenu à partir de l’attribut DefaultLocalRegistryRoot du VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Retourne le chemin d’accès du répertoire qui sert de référentiel commun pour [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] les données de l’utilisateur itinérant actuel, par exemple, C:\Documents and Settings \\ *YourAccountName*\Application Data\Microsoft\VisualStudio\8.0Exp.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Retourne le chemin d’accès du répertoire qui sert de référentiel commun pour [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] les données de l’utilisateur non itinérant actuel, par exemple, C:\Documents and Settings \\ *YourAccountName*\Local Settings\Application Data\Microsoft\VisualStudio\8.0Exp.  
  
## <a name="see-also"></a>Voir aussi  
 [État du VSPackage](../misc/vspackage-state.md)