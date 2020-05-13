---
title: Enregistrement des gestionnaires de commandement d’assemblage Interop (fr) Microsoft Docs
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
ms.openlocfilehash: 7e2ab6389f1e0d369dd095290d12c97431c44155
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705860"
---
# <a name="registering-interop-assembly-command-handlers"></a>Inscription des gestionnaires de commandes d’assemblys d’interopérabilité
Un VSPackage doit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] s’inscrire avec de sorte que l’environnement de développement intégré (IDE) achemine ses commandes correctement.

 Le registre peut être mis à jour soit par modification manuelle, soit par l’utilisation d’un fichier registraire (.rgs). Pour plus d'informations, consultez [Creating Registrar Scripts](/cpp/atl/creating-registrar-scripts).

 Le cadre de paquet géré (MPF) <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> fournit cette fonctionnalité à travers la classe.

- [Les](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) ressources de référence de format de tableau de commande sont situées dans des dlls d’interface utilisateur satellites non managés.

## <a name="command-handler-registration-of-a-vspackage"></a>Enregistrement du gestionnaire de commandement d’un VSPackage
 Un VSPackage agissant en tant que gestionnaire pour l’interface utilisateur (interface utilisateur) `GUID`commandes basées nécessite une entrée de registre nommé d’après le VSPackage . Cette inscription au registre précise l’emplacement du fichier de ressources de l’assurance-chômage du VSPackage et la ressource de menu dans ce fichier. L’entrée de registre elle-même est située sous HKEY_LOCAL_MACHINE\\-Software-Microsoft-VisualStudio*\<Version>* Menus, où [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] * \<la version>* est la version de , par exemple 9.0.

> [!NOTE]
> Le chemin de racine de HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio\\*\<Version>* peut être remplacé par [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] une racine alternative lorsque la coquille est parascée. Pour plus d’informations sur le chemin de racine, voir [installer VSPackages Avec Installateur Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>L’entrée du registre des ressources du CTMENU
 La structure de l’entrée du registre est :

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> est le `GUID` VSPackage sous la forme de XXXXXXX-XXXX-XXXX-XXXX-XXXX-XXXXX-XXXXXXXXXX.

 *L’information sur les ressources>se compose de trois éléments séparés par des virgules. \<* Ces éléments sont, dans l’ordre:

 \<*Path to Resource DLL*>, \< *Menu Resource ID* \<>, *Version Menu*>

 Le tableau suivant décrit \<les domaines de l’information *sur les ressources*>.

| Élément | Description |
|---------------------------| - |
| \<*Chemin vers la ressource DLL*> | Il s’agit de la voie complète vers la ressource DLL qui contient la ressource de menu ou cela est laissé vide, ce qui indique que la ressource DLL du VSPackage doit être utilisé (comme spécifié dans le sous-clé paquets où le VSPackage lui-même est enregistré).<br /><br /> Il est d’usage de laisser ce champ vide. |
| \<*Id de ressource de menu*> | Il s’agit de `CTMENU` l’ID de ressource de la ressource qui contient tous les éléments d’interface utilisateur pour le VSPackage tel qu’il est compilé à partir d’un fichier [.vsct.](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) |
| \<*Menu Version*> | Il s’agit d’un `CTMENU` nombre utilisé comme une version pour la ressource. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]utilise cette valeur pour déterminer si elle doit `CTMENU` réamerger le `CTMENU` contenu de la ressource avec son cache de toutes les ressources. Un réapparaître est déclenché par l’exécution de la commande de configuration devenv.<br /><br /> Cette valeur doit d’abord être réglée à 1 `CTMENU` et incrémentée après chaque changement dans la ressource et avant que le remerge se produise. |

### <a name="example"></a>Exemple
 Voici un exemple de quelques entrées de ressources :

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Voir aussi
- [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Commandes et menus utilisant des assemblys d’interopérabilité](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
