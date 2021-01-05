---
title: Inscription des gestionnaires de commandes d’assembly d’interopérabilité | Microsoft Docs
description: En savoir plus sur le contrat de commande de base utilisé par tous les VSPackages implémentant des commandes à l’aide d’assemblys d’interopérabilité.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b45fe06722b190569e067dccd325ba4acac4fb0f
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97875152"
---
# <a name="registering-interop-assembly-command-handlers"></a>Inscription des gestionnaires de commandes d’assemblys d’interopérabilité
Un VSPackage doit s’inscrire auprès de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] afin que l’environnement de développement intégré (IDE) achemine correctement ses commandes.

 Le registre peut être mis à jour par modification manuelle ou à l’aide d’un fichier d’inscription (. RGS). Pour plus d'informations, consultez [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

 Managed package Framework (MPF) fournit cette fonctionnalité par le biais de la <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> classe.

- Les ressources de [référence de format de table de commandes](/previous-versions/bb164647(v=vs.100)) se trouvent dans des dll d’interface utilisateur satellite non managées.

## <a name="command-handler-registration-of-a-vspackage"></a>Inscription du gestionnaire de commandes d’un VSPackage
 Un VSPackage agissant comme gestionnaire pour les commandes basées sur l’interface utilisateur requiert une entrée de Registre nommée après le VSPackage `GUID` . Cette entrée de Registre spécifie l’emplacement du fichier de ressources d’interface utilisateur du VSPackage et la ressource de menu dans ce fichier. L’entrée de Registre elle-même se trouve sous HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ *\<Version>* \Menus, où *\<Version>* est la version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , par exemple 9,0.

> [!NOTE]
> Le chemin d’accès racine de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\ *\<Version>* peut être substitué par une autre racine lorsque l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interpréteur de commandes est initialisé. Pour plus d’informations sur le chemin d’accès racine, consultez [installation de VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Entrée de registre de la ressource CTMENU
 La structure de l’entrée de Registre est la suivante :

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> est le `GUID` du VSPackage au format {xxxxxx-xxxx-xxxx-xxxx-XXXXXXXXX}.

 *\<Resource Information>* se compose de trois éléments séparés par des virgules. Ces éléments sont, dans l’ordre :

 \<*Path to Resource DLL*>, \<*Menu Resource ID*>, \<*Menu Version*>

 Le tableau suivant décrit les champs de \<*Resource Information*> .

| Élément | Description |
|---------------------------| - |
| \<*Path to Resource DLL*> | Il s’agit du chemin d’accès complet à la DLL de ressource qui contient la ressource de menu ou il est laissé vide, ce qui indique que la DLL de ressource du VSPackage doit être utilisée (comme spécifié dans la sous-clé packages où le VSPackage est enregistré).<br /><br /> Il est personnalisé pour laisser ce champ vide. |
| \<*Menu Resource ID*> | Il s’agit de l’ID de ressource de la `CTMENU` ressource qui contient tous les éléments d’interface utilisateur du VSPackage tels qu’ils sont compilés à partir d’un fichier [. vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) . |
| \<*Menu Version*> | Il s’agit d’un nombre utilisé comme version de la `CTMENU` ressource. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilise cette valeur pour déterminer si elle doit refusionner le contenu de la `CTMENU` ressource avec son cache de toutes les `CTMENU` ressources. Une refusion est déclenchée par l’exécution de la commande d’installation de devenv.<br /><br /> Cette valeur doit initialement être définie sur 1 et incrémentée après chaque modification de la `CTMENU` ressource et avant la refusion. |

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