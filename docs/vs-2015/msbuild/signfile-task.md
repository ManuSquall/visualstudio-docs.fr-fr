---
title: SignFile, tâche | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SignFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, SignFile task
- SignFile task [MSBuild]
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dc65715c2e0bc1e6e36e86c1ce8e3cd1b4c81058
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59660344"
---
# <a name="signfile-task"></a>SignFile, tâche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Signe le fichier spécifié à l'aide du certificat spécifié.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `SignFile` .  
  
 Notez que les certificats SHA-256 ne sont autorisés que sur les ordinateurs où est installé le .NET 4.5 et version ultérieure.  
  
> [!WARNING]
>  Depuis Visual Studio 2013 Update 3, cette tâche possède une nouvelle signature qui permet de spécifier la version cible de .NET Framework pour le fichier. Vous êtes encouragé à utiliser la nouvelle signature dans la mesure du possible, car le processus MSBuild n'utilise les hachages SHA-256 que lorsque la version cible du .NET Framework est .NET 4.5 ou version ultérieure. Si la version cible du .NET Framework est .NET 4.0 ou version antérieure, le hachage SHA-256 ne sera pas utilisé.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`CertificateThumbprint`|Paramètre `String` requis.<br /><br /> Spécifie le certificat à utiliser pour la signature. Ce certificat doit se trouver dans le magasin personnel de l'utilisateur actuel.|  
|`SigningTarget`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> requis.<br /><br /> Spécifie les fichiers à signer avec le certificat.|  
|`TimestampUrl`|Paramètre `String` facultatif.<br /><br /> Spécifie l'URL d'un serveur d'horodatage.|  
|`TargetFrameworkVersion`|Version du .NET Framework utilisée pour la cible.|  
  
## <a name="remarks"></a>Remarques  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Task, classe de base](../msbuild/task-base-class.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise la tâche `SignFile` pour signer les fichiers spécifiés dans la collection d'éléments `FilesToSign` avec le certificat spécifié par la propriété `Certificate`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <FileToSign Include="File.exe" />  
    </ItemGroup>  
    <PropertyGroup>  
        <Certificate>Cert.cer</Certificate>  
    </PropertyGroup>  
    <Target Name="Sign">  
        <SignFile  
            CertificateThumbprint="$(CertificateThumbprint)"  
            SigningTarget="@(FileToSign)"   
            TargetFrameworkVersion="v4.5" />  
    </Target>  
</Project>  
```  
  
> [!NOTE]
>  L'empreinte de certificat correspond au hachage SHA-1 du certificat. Pour plus d’informations, consultez [Obtenir le hachage SHA-1 d’un certificat d’autorité de certification racine de confiance](http://msdn.microsoft.com/dd641990-9a88-4228-a245-017797131a87).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise la tâche `Exec` pour signer les fichiers spécifiés dans la collection d'éléments `FilesToSign` avec le certificat spécifié par la propriété `Certificate`. Vous pouvez l'utiliser pour signer les fichiers Windows Installer pendant le processus de génération.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <FileToSign Include="File.msi" />  
    </ItemGroup>  
    <PropertyGroup>  
        <Certificate>Cert.cer</Certificate>  
    </PropertyGroup>  
    <Target Name="Sign">  
        <Exec Command="signtool.exe sign /f CertFile /p Password "@(FileToSign)" "/>  
        <SignFile  
            CertificateThumbprint="$(CertificateThumbprint)"  
            SigningTarget="@(FileToSign)"   
            TargetFrameworkVersion="v4.0" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)   
 [Tâches](../msbuild/msbuild-tasks.md)
