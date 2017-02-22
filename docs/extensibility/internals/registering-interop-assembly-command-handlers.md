---
title: "L&#39;inscription de gestionnaires de commandes d&#39;Assembly PIA | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assemblys PIA, les gestionnaires de commandes"
  - "gestion avec des assemblys PIA, l'enregistrement de commandes"
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# L&#39;inscription de gestionnaires de commandes d&#39;Assembly PIA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un VSPackage doit inscrire avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] afin que l'environnement de développement intégré \(IDE\) achemine ses commandes correctement.  
  
 Le Registre peut être mis à jour en modifiant manuellement ou à l'aide d'un fichier d'inscription \(.rgs\). Pour plus d'informations, consultez [Creating Registrar Scripts](/visual-cpp/atl/creating-registrar-scripts).  
  
 Managed Package Framework \(MPF\) fournit cette fonctionnalité via la <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> classe.  
  
 [Command Table Format Reference](http://msdn.microsoft.com/fr-fr/09e9c6ef-9863-48de-9483-d45b7b7c798f) ressources se trouvent dans des DLL de l'interface utilisateur de satellites non managé.  
  
## Enregistrement du Gestionnaire de commande d'un VSPackage  
 Un VSPackage agissant comme un gestionnaire pour l'interface utilisateur \(IU\)\-en fonction des commandes nécessite une entrée de Registre nommée d'après le VSPackage `GUID`. Cette entrée de Registre spécifie l'emplacement du fichier de ressources de l'interface utilisateur du VSPackage et la ressource de menu dans le fichier. L'entrée de Registre se trouve sous HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\VisualStudio\\*\< Version \>*\\Menus, où *\< Version \>* est la version de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], par exemple 9.0.  
  
> [!NOTE]
>  Le chemin d'accès racine de HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\< Version \>* peut être remplacée par une autre racine lorsque le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] shell est initialisé. Pour plus d'informations sur le chemin d'accès racine, consultez [Installation de packages VS avec Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
### L'entrée de Registre de ressource CTMENU  
 La structure de l'entrée de Registre est :  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\ Menus\ <GUID> = <Resource Information>  
```  
  
 \<*GUID*\> est le `GUID` du VSPackage sous la forme {XXXXXX\-XXXX\-XXXX\-XXXX\-XXXXXXXXX}.  
  
 *\> informations sur la ressource \<* se compose de trois éléments séparés par des virgules. Ces éléments sont, dans l'ordre :  
  
 \<*Chemin d'accès à la DLL de ressource*\>, \<*ID de ressource de Menu*\>, \<*Menu Version*\>  
  
 Le tableau suivant décrit les champs de \<*informations sur les ressources*\>.  
  
|Élément|Description|  
|-------------|-----------------|  
|\<*Chemin d'accès à la DLL de ressource*\>|Il s'agit du chemin d'accès complet à la DLL de ressource qui contient la ressource de menu ou de ce champ est laissé vide, indiquant que ressource du VSPackage DLL doit être utilisé \(comme spécifié dans la sous\-clé Packages où est enregistré le VSPackage lui\-même\).<br /><br /> Il est habituel de laisser ce champ vide.|  
|\<*ID de ressource de menu*\>|L'ID de ressource de la `CTMENU` ressources qui contient tous les éléments d'interface utilisateur pour le VSPackage comme compilé à partir d'un [.vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) fichier.|  
|\<*Menu Version*\>|Il s'agit d'un nombre utilisé comme une version pour le `CTMENU` ressource.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilise cette valeur pour déterminer s'il doit remerge le contenu de la `CTMENU` ressources avec son cache de tous les `CTMENU` ressources. Une remerge est déclenchée par l'exécution de la commande devenv.<br /><br /> Cette valeur doit être initialement définie sur 1 et incrémentée après chaque modification dans le `CTMENU` ressource et avant le remerge se produit.|  
  
### Exemple  
 Voici un exemple de deux entrées de ressources :  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\ Menus\ {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10 {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## Voir aussi  
 [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Commandes et des Menus qui utilisent des assemblys PIA](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)