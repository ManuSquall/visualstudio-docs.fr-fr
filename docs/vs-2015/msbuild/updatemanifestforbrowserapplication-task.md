---
title: UpdateManifestForBrowserApplication, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6dffa98a8abbf74bd6eee8761d91f09a7c022666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68740219"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> tâche est exécutée pour ajouter l' **\<hostInBrowser />** élément au manifeste d’application (*NomProjet*. exe. manifest) lors de la génération d’un [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] projet.  
  
## <a name="task-parameters"></a>Paramètres de tâche  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`ApplicationManifest`|Paramètre **ITaskItem []** obligatoire.<br /><br /> Spécifie le chemin d'accès et le nom du fichier manifeste d'application auquel ajouter l'élément `<hostInBrowser />`.|  
|`HostInBrowser`|Paramètre **Boolean** obligatoire.<br /><br /> Spécifie s’il faut modifier le manifeste d’application pour inclure l' **\<hostInBrowser />** élément. Si la **valeur est true**, un nouvel `<` élément **HostInBrowser/>** est inclus dans l' **\<entryPoint />** élément. Notez que l’inclusion des éléments est cumulative : si un **\<hostInBrowser />** élément existe déjà, il n’est pas supprimé ou remplacé. Au lieu de cela, un **\<hostInBrowser />** élément supplémentaire est créé. Si la valeur est **false**, le manifeste de l’application n’est pas modifié.|  
  
## <a name="remarks"></a>Notes  
 [!INCLUDE[TLA2#tla_xbap#plural](../includes/tla2sharptla-xbapsharpplural-md.md)] sont exécutés à l'aide du déploiement [!INCLUDE[TLA#tla_clickonce](../includes/tlasharptla-clickonce-md.md)] et, par conséquent, doivent être publiés avec les manifestes de déploiement et d'application correspondants. [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] utilise la tâche [GenerateApplicationManifest](/dotnet/api/microsoft.build.tasks.generateapplicationmanifest) pour générer un manifeste d’application.  
  
 Ensuite, pour configurer une application à héberger à partir d’un navigateur, un élément supplémentaire **\<hostInBrowser />** doit être ajouté au manifeste d’application, comme indiqué dans l’exemple suivant :  
  
```  
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
  
 La tâche <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> est exécutée quand un projet [!INCLUDE[TLA2#tla_xbap](../includes/tla2sharptla-xbap-md.md)] est généré pour ajouter l'élément `<hostInBrowser />`.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment s'assurer que l'élément `<hostInBrowser />` est inclus dans un fichier manifeste d'application.  
  
```  
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
 [Référence de tâche](../msbuild/wpf-msbuild-task-reference.md)   
 [Référence MSBuild](../msbuild/msbuild-reference.md)   
 [Référence de tâche](../msbuild/msbuild-task-reference.md)   
 [Génération d’une application WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Vue d'ensemble des applications de navigateur XAML](https://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
