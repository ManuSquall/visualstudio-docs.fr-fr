---
title: Cibler Visual Studio 2019 lors de la création d’une extension dans Visual Studio 2022 preview
description: Découvrez comment faire fonctionner votre extension Visual Studio avec Visual Studio 2019 si vous créez le projet avec Visual Studio 2022 preview.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: dcf556e271e6a805110eac0c978a845f2195e28f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308757"
---
# <a name="target-a-previous-version-when-creating-an-extension-in-visual-studio-2022-preview"></a>Cibler une version précédente lors de la création d’une extension dans Visual Studio 2022 preview

[!INCLUDE [preview-note](../includes/preview-note.md)]

Lorsque vous créez un projet VSIX à l’aide de Visual Studio 2022 Preview, le projet est créé à partir d’un modèle qui cible Visual Studio 2022. Si vous souhaitez cibler Visual Studio 2019 ou une version antérieure, vous devez modifier le projet créé.

Envisagez d’utiliser des [projets partagés](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting) pour cibler visual studio 2019 et visual studio 2022 tout en partageant la plupart ou la totalité du code de votre extension.

Procédez comme suit sur le projet VSIX qui doit cibler Visual Studio 2019 :

1. Modifiez le `source.extension.vsixmanifest` fichier pour supprimer l' `ProductArchitecture` élément et la plage de versions :

    ```diff
    -<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
    +<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[16.0,17.0)">
    -  <ProductArchitecture>amd64</ProductArchitecture>
     </InstallationTarget>
    ```

   Mettez également à jour les composants requis :

    ```diff
    -<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,18.0)" DisplayName="Visual Studio core editor" />
    +<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[16.0,17.0)" DisplayName="Visual Studio core editor" />
    ```

    Passez en revue le fichier pour toutes les autres mises à jour qui peuvent être nécessaires.

1. Modifiez les versions des packages du kit de développement logiciel (SDK) Visual Studio que vous référencez dans votre fichier projet :

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    ```
