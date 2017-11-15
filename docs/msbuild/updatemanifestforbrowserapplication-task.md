---
title: "UpdateManifestForBrowserApplication, tâche | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UpdateManifestForBrowserApplication task [WPF MSBuild]
- adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]
- building XBAP projects [WPF MSBuild]
- UpdateManifestForBrowserApplication task [WPF MSBuild], parameters
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
caps.latest.revision: "8"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 24430b3cfa74724dc8fc6ca3d92e5507c3f13514
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication, tâche
La tâche <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> est exécutée pour ajouter l’élément **\<hostInBrowser />** au manifeste d’application (*nom_projet*.exe.manifest) quand un projet [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] est généré.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`ApplicationManifest`|Paramètre **ITaskItem[]** obligatoire.<br /><br /> Spécifie le chemin d'accès et le nom du fichier manifeste d'application auquel ajouter l'élément `<hostInBrowser />`.|  
|`HostInBrowser`|Paramètre **Boolean** obligatoire.<br /><br /> Spécifie s’il faut modifier le manifeste de l’application pour inclure l’élément **\<hostInBrowser />**. Si la valeur est **true**, un nouvel élément `<`**hostInBrowser />** est inclus dans l’élément **\<entryPoint />**. Notez que l’inclusion des éléments est cumulative : si un élément **\<hostInBrowser />** existe déjà, il n’est ni supprimé ni remplacé. Au lieu de cela, un autre élément **\<hostInBrowser />** est créé. Si la valeur est **false**, le manifeste de l’application n’est pas modifié.|  
  
## <a name="remarks"></a>Notes  
 [!INCLUDE[TLA2#tla_xbap#plural](../msbuild/includes/tla2sharptla_xbapsharpplural_md.md)] sont exécutés à l'aide du déploiement [!INCLUDE[TLA#tla_clickonce](../msbuild/includes/tlasharptla_clickonce_md.md)] et, par conséquent, doivent être publiés avec les manifestes de déploiement et d'application correspondants. [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] utilise la tâche [GenerateApplicationManifest](http://msdn2.microsoft.com/library/6wc2ccdc.aspx) pour générer un manifeste d’application.  
  
 Ensuite, pour configurer une application hébergée par un navigateur, un élément supplémentaire, **\<hostInBrowser />**, doit être ajouté au manifeste de l’application, comme indiqué dans l’exemple suivant :  
  
```xml  
<!--MyXBAPApplication.exe.manifest-->  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly ... >  
    <asmv1:assemblyIdentity ... />  
    <application />  
    <entryPoint>  
      ...  
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />  
    </entryPoint>  
  ...  
/>  
```  
  
 La tâche <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> est exécutée quand un projet [!INCLUDE[TLA2#tla_xbap](../msbuild/includes/tla2sharptla_xbap_md.md)] est généré pour ajouter l'élément `<hostInBrowser />`.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment s'assurer que l'élément `<hostInBrowser />` est inclus dans un fichier manifeste d'application.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"  
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UpdateManifestForBrowserApplicationTask">  
    <UpdateManifestForBrowserApplication  
      ApplicationManifest="MyXBAPApplication.exe.manifest"  
      HostInBrowser="true" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur MSBuild WPF](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/wpf-msbuild-task-reference.md)   
 [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)   
 [Génération d’une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [Vue d’ensemble des applications du navigateur XAML WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)