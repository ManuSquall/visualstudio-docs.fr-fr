---
title: Fenêtres outil dans le registre | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cedb95ccd98c3d5bd5e05086cfd1b53b0f97cd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186384"
---
# <a name="tool-windows-in-the-registry"></a>Fenêtres Outil dans le Registre
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les VSPackages qui fournissent des fenêtres outil doivent s’inscrire auprès de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] en tant que fournisseurs de fenêtre outil. Les fenêtres outil créées à l’aide du modèle de package Visual Studio le font par défaut. Les fournisseurs de fenêtre outil ont des clés de Registre système qui spécifient des attributs de visibilité, tels que la taille et l’emplacement de la fenêtre outil par défaut, le GUID de la fenêtre qui sert de volet de la fenêtre outil et le style d’ancrage.  
  
 Pendant le développement, les fournisseurs de fenêtres outil managés enregistrent les fenêtres outil en ajoutant des attributs au code source, puis en exécutant l’utilitaire RegPkg.exe sur l’assembly résultant. Pour plus d’informations, consultez [inscription d’une fenêtre outil](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>Inscription des fournisseurs de fenêtres outil non managés  
 Les fournisseurs de fenêtres outil non managés doivent s’inscrire auprès [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] de dans la section ToolWindows du Registre système. Le fragment de fichier. reg suivant montre comment une fenêtre outil dynamique peut être inscrite :  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 Dans la première clé de l’exemple ci-dessus, le numéro de version est la version de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , par exemple 7,1 ou 8,0, la sous-clé {f0e1e9a1-9860-484D-ad5d-367d79aabf55} est le GUID du volet de la fenêtre outil (DynamicWindowPane), et la valeur par défaut {01069CDD-95CE-4620-AC21-DDFF6C57F012} est le GUID du VSPackage qui fournit la fenêtre outil. Pour obtenir une explication des sous-clés float et DontForceCreate, consultez Configuration de l’affichage de la [fenêtre outil](../extensibility/tool-window-display-configuration.md).  
  
 La deuxième clé facultative, ToolWindows\Visibility, spécifie les GUID des commandes qui nécessitent la visibilité de la fenêtre outil. Dans ce cas, aucune commande n’est spécifiée. Pour plus d’informations, consultez Configuration de l’affichage de la [fenêtre outil](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Essentiel des VSPackages](../misc/vspackage-essentials.md)
