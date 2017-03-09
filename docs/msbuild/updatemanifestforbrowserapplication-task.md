---
title: "UpdateManifestForBrowserApplication Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "UpdateManifestForBrowserApplication task [WPF MSBuild]"
  - "adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]"
  - "building XBAP projects [WPF MSBuild]"
  - "UpdateManifestForBrowserApplication task [WPF MSBuild], parameters"
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# UpdateManifestForBrowserApplication Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La tâche <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> est exécutée pour ajouter l'élément **\<hostInBrowser \/\>** au manifeste d'application \(*NomProjet*.exe.manifest\) quand un projet [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)] est généré.  
  
## Paramètres de tâche  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`ApplicationManifest`|Paramètre **ITaskItem\[\]** obligatoire.<br /><br /> Spécifie le chemin d'accès et le nom du fichier manifeste d'application auquel ajouter l'élément `<hostInBrowser />`.|  
|`HostInBrowser`|Paramètre **Boolean** obligatoire.<br /><br /> Spécifie s'il faut modifier le manifeste d'application pour inclure l'élément **\<hostInBrowser \/\>**.  Si la valeur est **true**, un nouvel élément `<`**hostInBrowser \/\>** est inclus dans l'élément **\<entryPoint \/\>**.  Notez que l'inclusion des éléments est cumulative : si un **\<hostInBrowser \/\>** existe déjà, il n'est pas supprimé ni remplacé.  Un autre élément **\<hostInBrowser \/\>** est plutôt créé.  Si la valeur est **false**, le manifeste d'application n'est pas modifié.|  
  
## Notes  
 [!INCLUDE[TLA2#tla_xbap#plural](../msbuild/includes/tla2sharptla_xbapsharpplural_md.md)] sont exécutés à l'aide du déploiement [!INCLUDE[TLA#tla_clickonce](../msbuild/includes/tlasharptla_clickonce_md.md)] et, par conséquent, doivent être publiés avec les manifestes de déploiement et d'application correspondants.  [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] utilise la tâche [GenerateApplicationManifest](http://msdn2.microsoft.com/library/6wc2ccdc.aspx) pour générer un manifeste d'application.  
  
 Ensuite, pour configurer une application de sorte à ce qu'elle soit hébergée depuis un navigateur, un élément supplémentaire, **\<hostInBrowser \/\>** doit être ajouté au manifeste d'application, comme indiqué dans l'exemple suivant :  
  
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
  
 La tâche <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> est exécutée quand un projet [!INCLUDE[TLA2#tla_xbap](../msbuild/includes/tla2sharptla_xbap_md.md)] est généré pour ajouter l'élément `<hostInBrowser />`.  
  
## Exemple  
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
  
## Voir aussi  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Génération d'une application WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [Vue d'ensemble des applications de navigateur XAML](../Topic/WPF%20XAML%20Browser%20Applications%20Overview.md)