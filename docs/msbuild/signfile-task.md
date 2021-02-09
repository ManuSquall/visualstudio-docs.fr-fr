---
title: SignFile, tâche | Microsoft Docs
description: Découvrez comment MSBuild utilise la tâche SignFile pour signer le fichier spécifié à l’aide du certificat spécifié.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9eef76a3757d9a2ff8ece5da5c18968097bd7618
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878160"
---
# <a name="signfile-task"></a>SignFile (tâche)

Signe le fichier spécifié à l'aide du certificat spécifié.

## <a name="parameters"></a>Paramètres

 Le tableau ci-dessous décrit les paramètres de la tâche `SignFile` .

 Notez que les certificats SHA-256 ne sont autorisés que sur les ordinateurs où est installé le .NET 4.5 et version ultérieure.

> [!WARNING]
> Depuis Visual Studio 2013 Update 3, cette tâche possède une nouvelle signature qui permet de spécifier la version cible de .NET Framework pour le fichier. Vous êtes encouragé à utiliser la nouvelle signature dans la mesure du possible, car le processus MSBuild n'utilise les hachages SHA-256 que lorsque la version cible du .NET Framework est .NET 4.5 ou version ultérieure. Si la version cible du .NET Framework est .NET 4.0 ou version antérieure, le hachage SHA-256 ne sera pas utilisé.

|Paramètre|Description|
|---------------|-----------------|
|`CertificateThumbprint`|Paramètre `String` requis.<br /><br /> Spécifie le certificat à utiliser pour la signature. Ce certificat doit se trouver dans le magasin personnel de l'utilisateur actuel.|
|`SigningTarget`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> requis.<br /><br /> Spécifie les fichiers à signer avec le certificat, de type. exe ou. dll.|
|`TimestampUrl`|Paramètre `String` facultatif.<br /><br /> Spécifie l'URL d'un serveur d'horodatage.|
|`TargetFrameworkVersion`|Version du .NET Framework utilisée pour la cible.|

## <a name="remarks"></a>Remarques

 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [classe de base de tâche](../msbuild/task-base-class.md).

## <a name="example"></a>Exemple

 L'exemple suivant utilise la tâche `SignFile` pour signer les fichiers spécifiés dans la collection d'éléments `FilesToSign` avec le certificat spécifié par la propriété `CertificateThumbprint`.

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
> L'empreinte de certificat correspond au hachage SHA-1 du certificat. Pour plus d’informations, voir [Obtenir le hachage SHA-1 d’un certificat d’autorité de certification racine de confiance](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc733076\(v\=ws.10\)). Si vous copiez et collez l’empreinte numérique à partir des détails du certificat, veillez à ne pas inclure le caractère invisible (3F) supplémentaire, ce qui risque d’empêcher `SignFile` de trouver le certificat.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
- [Tâches](../msbuild/msbuild-tasks.md)