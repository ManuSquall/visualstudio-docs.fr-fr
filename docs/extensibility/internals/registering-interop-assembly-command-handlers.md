---
title: Inscription des gestionnaires de commandes d’assembly d’interopérabilité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbc0d162a11df034bec4d1f357ef8abd106da401
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724687"
---
# <a name="registering-interop-assembly-command-handlers"></a>Inscription des gestionnaires de commandes d’assemblys d’interopérabilité
Un VSPackage doit s’inscrire auprès de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] afin que l’environnement de développement intégré (IDE) achemine correctement ses commandes.

 Le registre peut être mis à jour par modification manuelle ou à l’aide d’un fichier d’inscription (. RGS). Pour plus d'informations, consultez [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

 Managed package Framework (MPF) fournit cette fonctionnalité par le biais de la classe <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>.

- Les ressources de [référence de format de table de commandes](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) se trouvent dans des dll d’interface utilisateur satellite non managées.

## <a name="command-handler-registration-of-a-vspackage"></a>Inscription du gestionnaire de commandes d’un VSPackage
 Un VSPackage agissant comme gestionnaire pour les commandes basées sur l’interface utilisateur requiert une entrée de Registre nommée après le `GUID`VSPackage. Cette entrée de Registre spécifie l’emplacement du fichier de ressources d’interface utilisateur du VSPackage et la ressource de menu dans ce fichier. L’entrée de Registre elle-même se trouve sous HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ *\<version >* \Menus, où *\<version >* correspond à la version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], par exemple 9,0.

> [!NOTE]
> Le chemin d’accès racine de la version de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<* peut être substitué par une autre racine lorsque l’interpréteur de commandes [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] est initialisé. Pour plus d’informations sur le chemin d’accès racine, consultez [installation de VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Entrée de registre de la ressource CTMENU
 La structure de l’entrée de Registre est la suivante :

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> est le `GUID` du VSPackage sous la forme {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.

 *\<Resource informations >* se composent de trois éléments séparés par des virgules. Ces éléments sont, dans l’ordre :

 \<*chemin d’accès à la dll de ressource*>, \< l'*ID de ressource de menu*>, \< version de*menu* >

 Le tableau suivant décrit les champs de \<*informations sur les ressources*>.

| Élément | Description |
|---------------------------| - |
| \<*chemin d’accès à la dll de ressource* > | Il s’agit du chemin d’accès complet à la DLL de ressource qui contient la ressource de menu ou il est laissé vide, ce qui indique que la DLL de ressource du VSPackage doit être utilisée (comme spécifié dans la sous-clé packages où le VSPackage est enregistré).<br /><br /> Il est personnalisé pour laisser ce champ vide. |
| \< >*ID de ressource de menu* | Il s’agit de l’ID de ressource de la ressource `CTMENU` qui contient tous les éléments d’interface utilisateur du VSPackage, tels qu’ils sont compilés à partir d’un fichier [. vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) . |
| \< la*version du Menu* > | Il s’agit d’un nombre utilisé comme version de la ressource `CTMENU`. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilise cette valeur pour déterminer si elle doit refusionner le contenu de la ressource `CTMENU` avec son cache de toutes les ressources `CTMENU`. Une refusion est déclenchée par l’exécution de la commande d’installation de devenv.<br /><br /> Cette valeur doit initialement être définie sur 1 et incrémentée après chaque modification de la ressource `CTMENU` et avant la refusion. |

### <a name="example"></a>Exemple
 Voici un exemple de deux entrées de ressource :

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Voir aussi
- [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Commandes et menus utilisant des assemblys d’interopérabilité](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)