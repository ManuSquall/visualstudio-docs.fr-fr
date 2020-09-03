---
title: UpdateManifestForBrowserApplication, tâche | Microsoft Docs
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 079eecd6751f168a7beba32eda6d15eda712bd7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77631326"
---
# <a name="updatemanifestforbrowserapplication-task"></a>UpdateManifestForBrowserApplication, tâche

La <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> tâche est exécutée pour ajouter l' **\<hostInBrowser />** élément au manifeste d’application (* \<projectname> . exe. manifest*) lors de la génération d’un projet d’application de navigateur XAML (XBAP).

## <a name="task-parameters"></a>Paramètres de tâche

|Paramètre|Description|
|---------------|-----------------|
|`ApplicationManifest`|Paramètre **ITaskItem []** obligatoire.<br /><br /> Spécifie le chemin d'accès et le nom du fichier manifeste d'application auquel ajouter l'élément `<hostInBrowser />`.|
|`HostInBrowser`|Paramètre **Boolean** obligatoire.<br /><br /> Spécifie s’il faut modifier le manifeste d’application pour inclure l' **\<hostInBrowser />** élément. Si la **valeur est true**, un nouvel **\<hostInBrowser />** élément est inclus dans l' **\<entryPoint />** élément. L’inclusion d’élément est cumulative : si un **\<hostInBrowser />** élément existe déjà, il n’est pas supprimé ou remplacé. Au lieu de cela, un **\<hostInBrowser />** élément supplémentaire est créé. Si la valeur est **false**, le manifeste de l’application n’est pas modifié.|

## <a name="remarks"></a>Notes

 Les applications XBAP sont exécutées à l’aide du déploiement ClickOnce. elles doivent donc être publiées avec les manifestes de déploiement et d’application de prise en charge. MSBuild utilise la tâche [GenerateApplicationManifest](generateapplicationmanifest-task.md) pour générer un manifeste d’application.

 Ensuite, pour configurer une application à héberger à partir d’un navigateur, un **\<hostInBrowser />** élément supplémentaire doit être ajouté au manifeste d’application, comme illustré dans l’exemple suivant :

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

 La <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> tâche est exécutée lorsqu’un projet XBAP est généré afin d’ajouter l' `<hostInBrowser />` élément.

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

- [Informations de référence sur MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Informations de référence sur les tâches](../msbuild/wpf-msbuild-task-reference.md)
- [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Générer une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Vue d’ensemble des applications de navigateur XAML WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)