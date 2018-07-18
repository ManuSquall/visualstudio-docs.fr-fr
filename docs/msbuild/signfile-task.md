---
title: SignFile, tâche | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 329cef79c529850bbe90a62cc24d5ec989379aa9
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104176"
---
# <a name="signfile-task"></a>SignFile, tâche

Signe le fichier spécifié à l'aide du certificat spécifié.
  
## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche `SignFile`.
  
 Notez que les certificats SHA-256 ne sont autorisés que sur les ordinateurs où est installé le .NET 4.5 et version ultérieure.
  
> [!WARNING]
> Depuis Visual Studio 2013 Update 3, cette tâche possède une nouvelle signature qui permet de spécifier la version cible de .NET Framework pour le fichier. Vous êtes encouragé à utiliser la nouvelle signature dans la mesure du possible, car le processus MSBuild n'utilise les hachages SHA-256 que lorsque la version cible du .NET Framework est .NET 4.5 ou version ultérieure. Si la version cible du .NET Framework est .NET 4.0 ou version antérieure, le hachage SHA-256 ne sera pas utilisé.
  
|Paramètre|Description|
|---------------|-----------------|
|`CertificateThumbprint`|Paramètre `String` requis.<br /><br /> Spécifie le certificat à utiliser pour la signature. Ce certificat doit se trouver dans le magasin personnel de l'utilisateur actuel.|
|`SigningTarget`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> requis.<br /><br /> Spécifie les fichiers à signer avec le certificat.|
|`TimestampUrl`|Paramètre `String` facultatif.<br /><br /> Spécifie l'URL d'un serveur d'horodatage.|
|`TargetFrameworkVersion`|Version du .NET Framework utilisée pour la cible.|
  
## <a name="remarks"></a>Notes

 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [Task, classe de base](../msbuild/task-base-class.md).
  
## <a name="example"></a>Exemple

 L'exemple suivant utilise la tâche `SignFile` pour signer les fichiers spécifiés dans la collection d'éléments `FilesToSign` avec le certificat spécifié par la propriété `Certificate`.

```xml
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
> L'empreinte de certificat correspond au hachage SHA-1 du certificat. Pour plus d’informations, consultez [Obtenir le hachage SHA-1 d’un certificat d’autorité de certification racine de confiance](http://msdn.microsoft.com/en-us/dd641990-9a88-4228-a245-017797131a87).
  
## <a name="see-also"></a>Voir aussi  
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)   
 [Tâches](../msbuild/msbuild-tasks.md)