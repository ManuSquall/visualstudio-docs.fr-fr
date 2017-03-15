---
title: "Fenêtres Outil dans le Registre | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
caps.latest.revision: 12
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: dc99605a367bb3584f9766b50aa2a4ff382656c4
ms.lasthandoff: 02/22/2017

---
# <a name="tool-windows-in-the-registry"></a>Fenêtres Outil dans le Registre
Les packages VS qui fournissent des fenêtres Outil doivent enregistrer avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en tant que fournisseurs de fenêtre d’outils. Les fenêtres Outil créées en utilisant le modèle de Package Visual Studio cela par défaut. Les fournisseurs de fenêtre outil ont des clés de Registre qui spécifient les attributs de visibilité, telles que la taille de la fenêtre outil par défaut et l’emplacement, le GUID de la fenêtre qui sert le volet de fenêtre outil et le style d’ancrage.  
  
 Pendant le développement, fournisseurs de fenêtre outil gérée inscrivant les fenêtres Outil en ajout d’attributs au code source, puis en exécutant l’utilitaire RegPkg.exe sur l’assembly résultant. Pour plus d’informations, consultez [l’inscription d’une fenêtre outil](../extensibility/registering-a-tool-window.md).  
  
## <a name="registering-unmanaged-tool-window-providers"></a>L’enregistrement des fournisseurs de fenêtre outil non managé  
 Fournisseurs de fenêtre outil non managé doivent inscrire avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dans la section ToolWindows du Registre système. Le fragment de fichier .reg suivant montre comment une fenêtre outil dynamique peut être enregistrée :  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]  
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"  
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"  
"Float"="250, 250, 410, 430"  
"DontForceCreate"=dword:00000001  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]  
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000  
```  
  
 Dans la première clé dans l’exemple ci-dessus, le numéro de version est la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], 7.1 ou 8.0, par exemple la sous-clé {f0e1e9a1-9860-484d-ad5d-367d79aabf55} est le GUID du volet de fenêtre outil (DynamicWindowPane) et la valeur par défaut {01069cdd-95ce-4620-ac21-ddff6c57f012} est le GUID du package VS en fournissant la fenêtre outil. Pour obtenir une explication des sous-clés Float et DontForceCreate, consultez [outil de Configuration de l’affichage fenêtre](../extensibility/tool-window-display-configuration.md).  
  
 La deuxième clé facultatif, ToolWindows\Visibility, spécifie le GUID des commandes qui requièrent la fenêtre d’outils à rendre visible. Dans ce cas, il n’existe aucune commande spécifiée. Pour plus d’informations, consultez [outil de Configuration de l’affichage fenêtre](../extensibility/tool-window-display-configuration.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de base des VSPackages](../misc/vspackage-essentials.md)
