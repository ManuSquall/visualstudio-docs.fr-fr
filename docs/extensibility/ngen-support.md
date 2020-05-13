---
title: Soutien Ngen dans VSIX v3 Microsoft Docs
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb75b9256ca937106235fa7a7d66d9cec71c9c60
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702400"
---
# <a name="ngen-support-in-vsix-v3"></a>Prise en charge de Ngen dans VSIX v3

Avec Visual Studio 2017 et le nouveau format manifeste d’extension VSIX v3 (version 3), les développeurs d’extension peuvent désormais « ngen » leurs assemblages au moment de l’installation.

Voici un extrait de MSDN qui explique ce que «ngen» fait:

>Le native Image Generator (*Ngen.exe*) est un outil qui améliore les performances des applications gérées. *Ngen.exe* crée des images natives, qui sont des fichiers contenant le code machine spécifique au processeur compilé, et les installe dans le cache d’image indigène sur l’ordinateur local. Le runtime peut utiliser des images natives du cache plutôt que le compilateur juste-à-temps (JIT) pour compiler l'assembly d'origine.
>
>de [Ngen.exe (Native Image Generator)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Pour "ngen" un assemblage, le VSIX doit être installé "par instance par machine". Cela peut être activé en vérifiant la case `extension.vsixmanifest` à cocher "tous les utilisateurs" dans le concepteur:

![vérifier tous les utilisateurs](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Comment permettre à Ngen

Pour activer ngen pour un assemblage, vous pouvez utiliser la fenêtre **Propriétés** dans Visual Studio.

Il ya 4 propriétés qui peuvent être définies:

1. **Ngen** (Boolean) - Si c’est vrai, l’installateur Visual Studio va "ngen" l’assemblage.
2. **Application Ngen** (corde) - Ngen offre la possibilité d’utiliser le fichier *app.config* d’une application afin de résoudre les dépendances d’assemblage. Cette valeur doit être définie sur une application dont *l’app.config* vous souhaitez utiliser (par rapport à l’annuaire d’installation Visual Studio).
3. **Ngen Architecture** (enum) - L’architecture pour compiler votre assemblage. Les options sont: a. NotSpecified b. X86 c. X64 d. Tous
4. **Ngen Priority** (integer entre 1 et 3) - Le niveau de priorité Ngen est documenté aux [niveaux de priorité Ngen.exe](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels).

Voici un aperçu de la fenêtre **Propriétés** en action :

![ngen dans les propriétés](media/ngen-in-properties.png)

Cela ajoutera des métadonnées à la référence du projet à l’intérieur du fichier *.csproj* du projet VSIX :

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
> Vous pouvez modifier le fichier .csproj directement, si vous préférez.

## <a name="extra-information"></a>Informations supplémentaires

Les modifications apportées au concepteur de propriétés s’appliquent à plus que de simples références de projet; vous pouvez définir les métadonnées Ngen pour les éléments à l’intérieur de votre projet ainsi (en utilisant les mêmes méthodes décrites ci-dessus) tant que les éléments sont des assemblages .NET.
