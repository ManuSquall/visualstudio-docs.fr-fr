---
title: "Fenêtres Outil dans le Registre | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 38b4415a24a7440a2d3725fb1183863e7a337bbb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="tool-windows-in-the-registry"></a>Fenêtres Outil dans le Registre
VSPackages qui fournissent les fenêtres Outil doit enregistrer avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en tant que fournisseurs de fenêtre d’outils. Les fenêtres Outil créées en utilisant le modèle de Package Visual Studio cela par défaut. Fournisseurs de fenêtre outil ont des clés de Registre qui spécifient les attributs de visibilité, telles que la taille de la fenêtre outil par défaut et l’emplacement, le GUID de la fenêtre qui sert le volet de fenêtre outil et le style d’ancrage.  
  
 Pendant le développement, les fournisseurs de fenêtre outil gérée inscrire les fenêtres Outil en ajout d’attributs au code source, puis en exécutant l’utilitaire RegPkg.exe sur l’assembly résultant. Pour plus d’informations, consultez [l’inscription d’une fenêtre outil](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>L’enregistrement des fournisseurs de fenêtre outil non managé  
 Fournisseurs de fenêtre outil non managé doivent inscrire auprès de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dans la section ToolWindows du Registre système. Le fragment de fichier .reg suivant montre comment une fenêtre outil dynamique peut être inscrit :  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 Dans la première clé dans l’exemple ci-dessus, le numéro de version est la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], par exemple 7.1 ou 8.0, la sous-clé {f0e1e9a1-9860-484d-ad5d-367d79aabf55} est le GUID du volet de fenêtre outil (DynamicWindowPane) et le {de valeur par défaut 01069cdd-95ce-4620-Ac21-ddff6c57f012} est le GUID du VSPackage en fournissant la fenêtre outil. Pour obtenir une explication des sous-clés Float et DontForceCreate, consultez [affichage Configuration de la fenêtre outil](../extensibility/tool-window-display-configuration.md).  
  
 La deuxième clé facultatif, ToolWindows\Visibility, spécifie les GUID des commandes qui nécessitent la fenêtre d’outils à afficher. Dans ce cas, il n’existe aucune commande spécifiée. Pour plus d’informations, consultez [affichage Configuration de la fenêtre outil](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [VSPackages](../extensibility/internals/vspackages.md)