---
title: "Tâche GenerateApplicationManifest | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/msbuild/2003#GenerateApplicationManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateApplicationManifest task
- HostInBrowser property (MSBuild)
- GenerateApplicationManifest task [MSBuild]
ms.assetid: a494102b-0cb2-4755-8e2a-d2c0f39fac1d
caps.latest.revision: "24"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e0ae1ff71e2fb304849b70222fec7a4ce85c0560
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="generateapplicationmanifest-task"></a>GenerateApplicationManifest, tâche
Génère un manifeste d’application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ou un manifeste natif. Un manifeste natif décrit un composant en lui définissant une identité unique et en identifiant tous les assemblys et fichiers qui le composent. Un manifeste d’application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] étend un manifeste natif en indiquant le point d’entrée de l’application et en spécifiant le niveau de sécurité des applications.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `GenerateApplicationManifest`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AssemblyName`|Paramètre `String` facultatif.<br /><br /> Spécifie le champ `Name` de l’identité d’assembly pour le manifeste généré. Si vous ne spécifiez pas ce paramètre, le nom est déduit du paramètre `EntryPoint` ou `InputManifest`. Si aucun nom ne peut être créé, la tâche génère une erreur.|  
|`AssemblyVersion`|Paramètre `String` facultatif.<br /><br /> Spécifie le champ `Version` de l’identité d’assembly pour le manifeste généré. Si ce paramètre n’est pas spécifié, la valeur par défaut 1.0.0.0 est utilisée.|  
|`ClrVersion`|Paramètre `String` facultatif.<br /><br /> Indique la version minimale du CLR (Common Language Runtime) requise par l’application. La valeur par défaut est la version du CLR utilisée par le système de génération. Si la tâche génère un manifeste natif, ce paramètre est ignoré.|  
|`ConfigFile`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie l’élément contenant le fichier de configuration de l’application. Si la tâche génère un manifeste natif, ce paramètre est ignoré.|  
|`Dependencies`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie une liste d’éléments qui définit l’ensemble d’assemblys dépendants du manifeste généré. Chaque élément peut être décrit plus en détail par les métadonnées d’élément pour indiquer l’état de déploiement supplémentaire et le type de dépendance. Pour plus d’informations, consultez la section « Métadonnées d’élément » ci-dessous.|  
|`Description`|Paramètre `String` facultatif.<br /><br /> Spécifie la description de l’application ou du composant.|  
|`EntryPoint`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie un seul élément qui indique le point d’entrée de l’assembly de manifeste généré.<br /><br /> Pour un manifeste d’application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], ce paramètre spécifie l’assembly qui démarre quand l’application est exécutée.|  
|`ErrorReportUrl`|Paramètre <xref:System.String?displayProperty=fullName> facultatif.<br /><br /> Spécifie l’URL de la page web affichée dans les boîtes de dialogue pendant les rapports d’erreurs lors des installations ClickOnce.|  
|`FileAssociations`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie une liste d’un ou de plusieurs types de fichier associés au manifeste de déploiement ClickOnce.<br /><br /> Les associations de fichiers ne sont valides que si .NET Framework 3.5 ou version ultérieure est ciblé.|  
|`Files`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Fichiers à inclure dans le manifeste. Spécifiez le chemin complet pour chaque fichier.|  
|`HostInBrowser`|Paramètre <xref:System.Boolean> facultatif.<br /><br /> Si la valeur est `true`, l’application est hébergée dans un navigateur (comme le sont les applications de navigateur web WPF).|  
|`IconFile`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Indique le fichier icône de l’application. L’icône de l’application est exprimée dans le manifeste d’application généré et utilisée pour le menu Démarrer et la boîte de dialogue Ajouter ou supprimer des programmes. Si cette entrée n’est pas spécifiée, une icône par défaut est utilisée. Si la tâche génère un manifeste natif, ce paramètre est ignoré.|  
|`InputManifest`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Indique un document XML d’entrée à utiliser comme base pour le générateur de manifeste. Des données structurées telles que des définitions de manifeste personnalisées ou de sécurité d’application peuvent ainsi être reflétées dans le manifeste de sortie. L’élément racine dans le document XML doit être un nœud d’assembly dans l’espace de noms asmv1.|  
|`IsolatedComReferences`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Spécifie des composants COM à isoler dans le manifeste généré. Ce paramètre prend en charge l’isolation des composants COM pour le déploiement « COM sans inscription ». Cela consiste à générer automatiquement un manifeste avec des définitions d’inscription COM standard. Toutefois, les composants COM doivent être enregistrés sur l’ordinateur de génération pour que cela fonctionne correctement.|  
|`ManifestType`|Paramètre `String` facultatif.<br /><br /> Spécifie le type de manifeste à générer. Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Si ce paramètre n’est pas spécifié, la tâche sélectionne par défaut `ClickOnce`.|  
|`MaxTargetPath`|Paramètre `String` facultatif.<br /><br /> Spécifie la longueur maximale autorisée d’un chemin de fichier dans un déploiement d’applications [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Si cette valeur est spécifiée, la longueur de chaque chemin de fichier dans l’application est comparée à cette limite. Tout élément qui dépasse la limite génère un avertissement de génération. Si cette entrée n’est pas spécifiée ou est égale à zéro, aucune vérification n’est effectuée. Si la tâche génère un manifeste natif, ce paramètre est ignoré.|  
|`OSVersion`|Paramètre `String` facultatif.<br /><br /> Spécifie la version minimale de système d’exploitation requise par l’application. Par exemple, la valeur 5.1.2600.0 indique le système d’exploitation Windows XP. Si ce paramètre n’est pas spécifié, la valeur 4.10.0.0 est utilisée ; celle-ci représente Windows 98 Deuxième Édition, le système d’exploitation minimal pris en charge par le .NET Framework. Si la tâche génère un manifeste natif, cette entrée est ignorée.|  
|`OutputManifest`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le nom du fichier manifeste de sortie généré. Si vous ne spécifiez pas ce paramètre, le nom du fichier de sortie est déduit de l’identité du manifeste généré.|  
|`Platform`|Paramètre `String` facultatif.<br /><br /> Spécifie la plateforme cible de l’application. Ce paramètre peut avoir les valeurs suivantes :<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Si ce paramètre n’est pas spécifié, la tâche sélectionne par défaut `AnyCPU`.|  
|`Product`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom de l’application. Si vous ne spécifiez pas ce paramètre, le nom est déduit de l’identité du manifeste généré. Ce nom est utilisé comme nom du raccourci dans le menu Démarrer. Il fait partie du nom qui apparaît dans la boîte de dialogue Ajout/Suppression de programmes.|  
|`Publisher`|Paramètre `String` facultatif.<br /><br /> Spécifie l’éditeur de l’application. Si vous ne spécifiez pas ce paramètre, le nom est déduit de l’utilisateur enregistré ou de l’identité du manifeste généré. Ce nom est utilisé comme nom du dossier dans le menu Démarrer. Il fait partie du nom qui apparaît dans la boîte de dialogue Ajout/Suppression de programmes.|  
|`RequiresMinimumFramework35SP1`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est true, l’application requiert .NET Framework 3.5 SP1 ou une version plus récente.|  
|`TargetCulture`|Paramètre `String` facultatif.<br /><br /> Identifie la culture de l’application et spécifie le champ `Language` de l’identité d’assembly pour le manifeste généré. Si ce paramètre n’est pas spécifié, il est supposé que l’application est indifférente quant à la culture.|  
|`TargetFrameworkMoniker`|Paramètre `String` facultatif.<br /><br /> Spécifie le moniker de la version cible de .NET Framework.|  
|`TargetFrameworkProfile`|Paramètre `String` facultatif.<br /><br /> Spécifie le profil de la version cible de .NET Framework.|  
|`TargetFrameworkSubset`|Paramètre `String` facultatif.<br /><br /> Spécifie le nom du sous-ensemble du .NET Framework à cibler.|  
|`TargetFrameworkVersion`|Paramètre `String` facultatif.<br /><br /> Spécifie la version cible de .NET Framework du projet.|  
|`TrustInfoFile`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Indique un document XML qui définit la sécurité de l’application. L’élément racine dans le document XML doit être un nœud trustInfo dans l’espace de noms asmv2. Si la tâche génère un manifeste natif, ce paramètre est ignoré.|  
|`UseApplicationTrust`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est true, les propriétés `Product`, `Publisher` et `SupportUrl` sont écrites dans le manifeste de l’application.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.GenerateManifestBase>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste des paramètres de la classe Task, consultez [Task, classe de base](../msbuild/task-base-class.md).  
  
 Pour plus d’informations sur l’utilisation de la tâche `GenerateDeploymentManifest`, consultez [Tâche GenerateApplicationManifest](../msbuild/generateapplicationmanifest-task.md).  
  
 Les entrées des dépendances et des fichiers peuvent être complétées par des métadonnées d’élément pour spécifier un état de déploiement supplémentaire pour chaque élément.  
  
## <a name="item-metadata"></a>Métadonnées d’élément  
  
|Nom des métadonnées|Description|  
|-------------------|-----------------|  
|`DependencyType`|Indique si la dépendance est publiée et installée avec l’application ou un élément préalable requis. Ces métadonnées sont valides pour toutes les dépendances, mais elles ne sont pas utilisées pour les fichiers. Les valeurs disponibles pour ces métadonnées sont les suivantes :<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Install est la valeur par défaut.|  
|`AssemblyType`|Indique si la dépendance est un assembly managé ou natif. Ces métadonnées sont valides pour toutes les dépendances, mais elles ne sont pas utilisées pour les fichiers. Les valeurs disponibles pour ces métadonnées sont les suivantes :<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> La valeur par défaut, `Unspecified`, indique que le générateur de manifeste détermine automatiquement le type d’assembly.|  
|`Group`|Indique le groupe pour le téléchargement de fichiers supplémentaires à la demande. Le nom de groupe est défini par l’application et peut être une chaîne quelconque. Une chaîne vide indique que le fichier ne fait pas partie d’un groupe de téléchargement, ce qui représente la valeur par défaut. Les fichiers qui ne sont pas compris dans un groupe font partie du téléchargement d’application initial. Les fichiers d’un groupe sont téléchargés uniquement quand l’application le demande explicitement à l’aide de <xref:System.Deployment.Application>.<br /><br /> Ces métadonnées sont valides pour tous les fichiers pour lesquels `IsDataFile` a la valeur `false` et toutes les dépendances pour lesquelles `DependencyType` a la valeur `Install`.|  
|`TargetPath`|Spécifie comment le chemin doit être défini dans le manifeste généré. Cet attribut est valide pour tous les fichiers. Si cet attribut n’est pas spécifié, la spécification d’élément est utilisée. Cet attribut est valide pour tous les fichiers et dépendances dont `DependencyType` a la valeur `Install`.|  
|`IsDataFile`|Valeur de métadonnées `Boolean` qui indique si le fichier est un fichier de données. Un fichier de données est spécial dans la mesure où il est migré entre des mises à jour de l’application. Ces métadonnées sont uniquement valides pour les fichiers. `False` est la valeur par défaut.|  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la tâche `GenerateApplicationManifest` pour générer un manifeste d’application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] et la tâche `GenerateDeploymentManifest` pour générer un manifeste de déploiement pour une application ayant un assembly unique. Il utilise ensuite la tâche `SignFile` pour signer les manifestes.  
  
 Ceci illustre le scénario de génération de manifeste le plus simple dans lequel les manifestes [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sont générés pour un programme unique. Le nom et l’identité par défaut du manifeste sont déduits à partir de l’assembly.  
  
> [!NOTE]
>  Dans l’exemple ci-dessous, tous les fichiers binaires d’application sont prédéfinis, ce qui permet de mettre l’accent sur la génération de manifeste. Cet exemple produit un déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] complètement actif.  
  
> [!NOTE]
>  Pour plus d’informations sur la propriété `Thumbprint` utilisée dans la tâche `SignFile` de cet exemple, consultez [Tâche Signfile](../msbuild/signfile-task.md).  
  
```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            EntryPoint="@(EntryPoint)">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            EntryPoint="@(ApplicationManifest)">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise les tâches `GenerateApplicationManifest` et `GenerateDeploymentManifest` pour générer l’application et les manifestes de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] d’une application ayant un assembly unique, en spécifiant le nom et l’identité des manifestes.  
  
 Cet exemple est semblable à l’exemple précédent, si ce n’est que le nom et l’identité des manifestes sont explicitement spécifiés. En outre, cet exemple est configuré comme une application en ligne au lieu d’une application installée.  
  
> [!NOTE]
>  Dans l’exemple ci-dessous, tous les fichiers binaires d’application sont prédéfinis, ce qui permet de mettre l’accent sur la génération de manifeste. Cet exemple produit un déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] complètement actif.  
  
> [!NOTE]
>  Pour plus d’informations sur la propriété `Thumbprint` utilisée dans la tâche `SignFile` de cet exemple, consultez [Tâche Signfile](../msbuild/signfile-task.md).  
  
```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            EntryPoint="@(EntryPoint)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
                AssemblyName="SimpleWinApp.application"  
                AssemblyVersion="1.0.0.0"  
                EntryPoint="@(ApplicationManifest)"  
                Install="false"  
                OutputManifest="SimpleWinApp.application">  
                <Output  
                    ItemName="DeployManifest"  
                    TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise les tâches `GenerateApplicationManifest` et `GenerateDeploymentManifest` pour générer l’application et les manifestes de déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] d’une application avec plusieurs fichiers et assemblys.  
  
> [!NOTE]
>  Dans l’exemple ci-dessous, tous les fichiers binaires d’application sont prédéfinis, ce qui permet de mettre l’accent sur la génération de manifeste. Cet exemple produit un déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] complètement actif.  
  
> [!NOTE]
>  Pour plus d’informations sur la propriété `Thumbprint` utilisée dans la tâche `SignFile` de cet exemple, consultez [Tâche Signfile](../msbuild/signfile-task.md).  
  
```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
        <DeployUrl>  
            <!-- Insert the deployment URL here -->  
        </DeployUrl>  
        <SupportUrl>  
            <!-- Insert the support URL here -->  
        </SupportUrl>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe"/>  
        <Dependency Include="ClassLibrary1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <Dependency Include="ClassLibrary2.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <Group>Secondary</Group>  
        </Dependency>  
        <Dependency Include="MyAddIn1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <TargetPath>Addins\MyAddIn1.dll</TargetPath>  
        </Dependency>  
        <Dependency Include="ClassLibrary3.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Prerequisite</DependencyType>  
        </Dependency>  
  
        <File Include="Text1.txt">  
            <TargetPath>Text\Text1.txt</TargetPath>  
            <Group>Text</Group>  
        </File>  
        <File Include="DataFile1.xml ">  
            <TargetPath>Data\DataFile1.xml</TargetPath>  
            <IsDataFile>true</IsDataFile>  
        </File>  
  
        <IconFile Include="Heart.ico"/>  
        <ConfigFile Include="app.config">  
            <TargetPath>SimpleWinApp.exe.config</TargetPath>  
        </ConfigFile>  
        <BaseManifest Include="app.manifest"/>  
    </ItemGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            ConfigFile="@(ConfigFile)"  
            Dependencies="@(Dependency)"  
            Description="TestApp"  
            EntryPoint="@(EntryPoint)"  
            Files="@(File)"  
            IconFile="@(IconFile)"  
            InputManifest="@(BaseManifest)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            AssemblyName="SimpleWinApp.application"  
            AssemblyVersion="1.0.0.0"  
            DeploymentUrl="$(DeployToUrl)"  
            Description="TestDeploy"  
            EntryPoint="@(ApplicationManifest)"  
            Install="true"  
            OutputManifest="SimpleWinApp.application"  
            Product="SimpleWinApp"  
            Publisher="Microsoft"  
            SupportUrl="$(SupportUrl)"  
            UpdateEnabled="true"  
            UpdateInterval="3"  
            UpdateMode="Background"  
            UpdateUnit="weeks">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la tâche `GenerateApplicationManifest` pour générer un manifeste natif de l’application Test.exe, en référençant le composant natif Alpha.dll et un composant COM isolé Bravo.dll.  
  
 Cet exemple crée Test.exe.manifest, qui permet de déployer l’application XCOPY dans un déploiement COM sans inscription.  
  
> [!NOTE]
>  Dans l’exemple ci-dessous, tous les fichiers binaires d’application sont prédéfinis, ce qui permet de mettre l’accent sur la génération de manifeste. Cet exemple produit un déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] complètement actif.  
  
```xml  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <File Include="Test.exe" />  
        <Dependency Include="Alpha.dll">  
            <AssemblyType>Native</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <ComComponent Include="Bravo.dll" />  
    </ItemGroup>  
  
    <Target Name="Build">  
        <GenerateApplicationManifest  
            AssemblyName="Test.exe"  
            AssemblyVersion="1.0.0.0"  
            Dependencies="@(Dependency)"  
            Files="@(File)"  
            IsolatedComReferences="@(ComComponent)"  
            ManifestType="Native">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Tâche GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)   
 [SignFile, tâche](../msbuild/signfile-task.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)