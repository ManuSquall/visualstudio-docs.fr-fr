---
title: Prise en charge de la persistance de l’état | Microsoft Docs
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953803"
---
# <a name="support-for-state-persistence"></a>Prise en charge de la persistance de l’état
[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] peut mettre à jour l’état d’objets communs. Par exemple, les propriétés de solution et projet sont enregistrées dans et restaurées à partir des fichiers solution et projet. Paramètres de l’utilisateur peuvent exportés vers et importés à partir de fichiers de paramètres.  
  
 VSPackages reposent généralement sur le stockage local, dans le Registre système ou dans le dossier de données d’application pour l’utilisateur actuel ou l’ordinateur. Valeurs qui nécessitent une petite quantité d’espace de stockage, tels que des entiers et des chaînes sont généralement stockées dans le Registre système. Les valeurs qui nécessitent beaucoup d’espace pour le stockage, telles que les bitmaps, sont enregistrées dans un fichier. Le chemin d’accès du fichier peut lui-même être enregistré dans le Registre système. Le mécanisme de persistance doit être autorisé à accéder au stockage local.  
  
## <a name="support-for-locating-local-storage"></a>Prise en charge pour la localisation de stockage Local  
 Le <xref:Microsoft.VisualStudio.Shell.Package> classe prend en charge la localisation des informations d’état dans le dossier système de données du Registre ou une application pour l’utilisateur actuel ou l’ordinateur.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A>  
 Retourne le chemin d’accès de la racine de Registre de l’ordinateur local pour [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], par exemple, HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0Exp.  
  
 La racine de Registre local est obtenue à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> service. Si ce n’est pas disponible, elle est obtenue à partir de la <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> attribut du VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>  
 Retourne le chemin d’accès de l’utilisateur actuel (par ordinateur) racine du Registre pour [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], par exemple, HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp.  
  
 La racine de Registre local est obtenue à partir de la <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> service. Si ce n’est pas disponible, il est obtenu à partir de l’attribut DefaultLocalRegistryRoot du VSPackage.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserDataPath%2A>  
 Retourne le chemin d’accès du répertoire qui sert de référentiel commun pour [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] les données de l’utilisateur itinérant actuel, par exemple, C:\Documents and Settings\\*YourAccountName*\Application VisualStudio\8.0Exp.  
  
 <xref:Microsoft.VisualStudio.Shell.Package.UserLocalDataPath%2A>  
 Retourne le chemin d’accès du répertoire qui sert de référentiel commun pour [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] les données de l’utilisateur en cours non itinérant, par exemple, C:\Documents and Settings\\*YourAccountName*\Local Settings\Application Data\Microsoft\VisualStudio\8.0Exp.  
  
## <a name="see-also"></a>Voir aussi  
 [État du VSPackage](../misc/vspackage-state.md)