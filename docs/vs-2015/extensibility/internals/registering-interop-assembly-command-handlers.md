---
title: L’inscription de gestionnaires de commandes d’Assembly d’interopérabilité | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cfb8b493190429f6f3a0a6295d65db2c151639c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436612"
---
# <a name="registering-interop-assembly-command-handlers"></a>Inscription des gestionnaires de commandes d’assemblys d’interopérabilité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un VSPackage doit inscrire avec [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] afin que l’environnement de développement intégré (IDE) achemine ses commandes correctement.  
  
 Le Registre peut être mis à jour par une modification manuelle ou à l’aide d’un fichier d’inscription (.rgs). Pour plus d'informations, consultez [Creating Registrar Scripts](http://msdn.microsoft.com/library/cbd5024b-8061-4a71-be65-7fee90374a35).  
  
 Managed Package Framework (MPF) fournit cette fonctionnalité via le <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> classe.  
  
 [Référence de Format de Table de la commande](http://msdn.microsoft.com/09e9c6ef-9863-48de-9483-d45b7b7c798f) ressources se trouvent dans la DLL de l’interface utilisateur de satellites non managé.  
  
## <a name="command-handler-registration-of-a-vspackage"></a>Inscription du Gestionnaire de commande d’un VSPackage  
 Un VSPackage agissant comme un gestionnaire pour l’interface utilisateur (IU)-en fonction des commandes nécessite une entrée de Registre nommée d’après le VSPackage `GUID`. Cette entrée de Registre spécifie l’emplacement du fichier de ressources de l’interface utilisateur du VSPackage et de la ressource de menu dans ce fichier. L’entrée de Registre elle-même se trouve sous HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<Version >* \Menus, où  *\<Version >* est la version de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], par exemple 9.0.  
  
> [!NOTE]
> Le chemin d’accès racine de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version >* peut être remplacée par une autre racine quand le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] shell est initialisé. Pour plus d’informations sur le chemin d’accès racine, consultez [installation les VSPackages avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
### <a name="the-ctmenu-resource-registry-entry"></a>L’entrée de Registre de ressource CTMENU  
 La structure de l’entrée de Registre est :  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\  
  Menus\  
    <GUID> = <Resource Information>  
```  
  
 \<*GUID*> est le `GUID` du VSPackage sous la forme {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.  
  
 *\<Informations sur les ressources >* se compose de trois éléments séparés par des virgules. Ces éléments sont, dans l’ordre :  
  
 \<*Chemin d’accès à la DLL de ressource*>, \< *ID de ressource de Menu*>, \< *Menu Version*>  
  
 Le tableau suivant décrit les champs de \< *informations sur les ressources*>.  
  
|Élément|Description|  
|-------------|-----------------|  
|\<*Chemin d’accès à la DLL de ressource*>|Il s’agit du chemin d’accès complet à la DLL de ressource qui contient la ressource de menu ou il est vide, indiquant que les ressources du VSPackage DLL doit être utilisée (comme spécifié dans la sous-clé de Packages dans laquelle le VSPackage lui-même est enregistré).<br /><br /> Il est habituel de laisser ce champ vide.|  
|\<*ID de ressource de menu*>|Il s’agit d’ID de ressource de la `CTMENU` ressource qui contient tous les éléments d’interface utilisateur pour le VSPackage comme compilé à partir d’un [.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) fichier.|  
|\<*Menu Version*>|Il s’agit d’un nombre utilisé comme une version pour le `CTMENU` ressource. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utilise cette valeur pour déterminer s’il doit remerge le contenu de la `CTMENU` ressource avec son cache de tous les `CTMENU` ressources. Un remerge est déclenchée en exécutant la commande d’installation de devenv.<br /><br /> Cette valeur doit être initialement définie sur 1 et incrémentée après chaque modification dans le `CTMENU` ressource et avant le remerge se produit.|  
  
### <a name="example"></a>Exemple  
 Voici un exemple de deux entrées de ressources :  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Comment VSPackages ajoute des éléments d’Interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Commandes et menus utilisant des assemblys d’interopérabilité](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
