---
title: Outil Windows dans le Registre | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering
ms.assetid: c4bb8add-7148-49e4-a377-01d059fd5524
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: adb79fec233171a0d20e817f9675aaab8e7228f8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693163"
---
# <a name="tool-windows-in-the-registry"></a>Windows d’outil dans le Registre
Les VSPackages qui fournissent des fenêtres Outil doit enregistrer avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] en tant que fournisseurs de fenêtre d’outils. Les fenêtres Outil créées en utilisant le modèle de Package Visual Studio cela par défaut. Fournisseurs de fenêtre outil ont des clés de Registre système qui spécifient les attributs de visibilité, telles que la taille de la fenêtre outil par défaut et l’emplacement, le GUID de la fenêtre qui sert le volet de fenêtre outil et le style d’ancrage.

 Pendant le développement, les fournisseurs de fenêtre outil gérée inscrire les fenêtres Outil en ajout d’attributs au code source, puis en exécutant l’utilitaire RegPkg.exe sur l’assembly résultant. Pour plus d’informations, consultez [l’inscription d’une fenêtre outil](../extensibility/registering-a-tool-window.md).

## <a name="registering-unmanaged-tool-window-providers"></a>Inscription des fournisseurs de fenêtre outil non managé
 Fournisseurs de fenêtre outil non managé doivent inscrire avec [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dans la section ToolWindows du Registre système. Le fragment de fichier .reg suivant montre comment une fenêtre outil dynamique peut être inscrit :

```
- [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\<version number>\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}]
@="{01069cdd-95ce-4620-ac21-ddff6c57f012}"
"Name"="Microsoft.Samples.VisualStudio.IDE.ToolWindow.DynamicWindowPane"
"Float"="250, 250, 410, 430"
"DontForceCreate"=dword:00000001

- [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\ToolWindows\{f0e1e9a1-9860-484d-ad5d-367d79aabf55}\Visibility]
"{f1536ef8-92ec-443c-9ed7-fdadf150da82}"=dword:00000000
```

 Dans la première clé dans l’exemple ci-dessus, le numéro de version est la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], par exemple 7.1 ou 8.0, la sous-clé {f0e1e9a1-9860-484d-ad5d-367d79aabf55} est le GUID du volet de fenêtre outil (DynamicWindowPane) et la {de valeur par défaut 01069cdd-95ce-4620-Ac21-ddff6c57f012} est le GUID du VSPackage pour fournir la fenêtre outil. Pour obtenir une explication des sous-clés DontForceCreate et à virgule flottante, consultez [affichage Configuration de la fenêtre outil](../extensibility/tool-window-display-configuration.md).

 La deuxième clé facultative, ToolWindows\Visibility, spécifie le GUID des commandes qui nécessitent la fenêtre outil à rendre visible. Dans ce cas, il n’existe aucune commande spécifiée. Pour plus d’informations, consultez [affichage Configuration de la fenêtre outil](../extensibility/tool-window-display-configuration.md).

## <a name="see-also"></a>Voir aussi
- [VSPackages](../extensibility/internals/vspackages.md)