---
title: Prise en charge de NGen dans VSIX v3 | Microsoft Docs
description: Découvrez comment activer Native Image Generator, un outil que les développeurs d’extensions peuvent utiliser pour améliorer les performances des applications managées.
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 064176a0a28e3621e796bf60ede552f9cda155b0
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97864032"
---
# <a name="ngen-support-in-vsix-v3"></a>Prise en charge de Ngen dans VSIX v3

Avec Visual Studio 2017 et le nouveau format de manifeste d’extension VSIX v3 (version 3), les développeurs d’extensions peuvent désormais « Ngen » leurs assemblys au moment de l’installation.

Voici un extrait de MSDN qui explique ce que fait « Ngen » :

>Le générateur d’images natives (*Ngen.exe*) est un outil qui améliore les performances des applications managées. *Ngen.exe* crée des images natives, qui sont des fichiers contenant du code machine compilé spécifique au processeur, et les installe dans le cache des images natives sur l’ordinateur local. Le runtime peut utiliser des images natives du cache plutôt que le compilateur juste-à-temps (JIT) pour compiler l'assembly d'origine.
>
>à partir de [Ngen.exe (générateur d’images natives)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Pour « Ngen » un assembly, l’extension VSIX doit être installée « par ordinateur ». Vous pouvez activer cette option en cochant la case « tous les utilisateurs » dans le `extension.vsixmanifest` Concepteur :

![vérifier tous les utilisateurs](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Comment activer Ngen

Pour activer ngen pour un assembly, vous pouvez utiliser la fenêtre **Propriétés** dans Visual Studio.

Il y a 4 propriétés qui peuvent être définies :

1. **Ngen** (booléen)-si la valeur est true, le programme d’installation de Visual Studio « Ngen » l’assembly.
2. **Application Ngen** (String)-Ngen offre la possibilité d’utiliser le fichier *app.config* d’une application pour résoudre les dépendances d’assembly. Cette valeur doit être définie sur une application dont vous souhaitez utiliser les *app.config* (par rapport au répertoire d’installation de Visual Studio).
3. **Architecture Ngen** (enum) : architecture permettant de compiler votre assembly en mode natif. Les options sont : a. NotSpecified b. C x86. X64 d. Tous
4. **Priorité Ngen** (entier compris entre 1 et 3)-le niveau de priorité Ngen est documenté à [Ngen.exe niveaux de priorité](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels).

Voici un aperçu de la fenêtre **Propriétés** en action :

![Ngen dans les propriétés](media/ngen-in-properties.png)

Cela permet d’ajouter des métadonnées à la référence de projet à l’intérieur du fichier *. csproj* du projet VSIX :

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
```

> [!NOTE]
> Vous pouvez modifier le fichier. csproj directement, si vous préférez.

## <a name="extra-information"></a>Informations supplémentaires

Les modifications du concepteur de propriétés s’appliquent à plus que simplement des références de projet. vous pouvez également définir les métadonnées ngen pour les éléments à l’intérieur de votre projet (à l’aide des mêmes méthodes que celles décrites ci-dessus), à condition que les éléments soient des assemblys .NET.
