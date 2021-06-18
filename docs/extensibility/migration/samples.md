---
title: Exemple ImageOptimizer pour la mise à jour des extensions Visual Studio
description: Suivez un exemple pour apprendre à mettre à jour une extension Visual Studio pour utiliser Visual Studio 2022 preview.
ms.date: 06/08/2021
ms.topic: sample
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 8df7c20e93073ab2fc6a727e29f738a4313fd1d7
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308769"
---
# <a name="imageoptimizer---update-a-visual-studio-extension-step-by-step"></a>ImageOptimizer-mettre à jour une extension Visual Studio étape par étape

[!INCLUDE [preview-note](../includes/preview-note.md)]

Ce guide présente toutes les étapes requises pour l’ajout de la prise en charge de Visual Studio 2022 tout en maintenant la prise en charge de Visual Studio 2019 à l’aide de l’extension d’optimiseur d’image comme étude de cas.  
Il s’agit d’un guide approfondi avec les liens de validation git à chaque étape, mais vous êtes libre de voir le PR finalisé ici : [https://github.com/madskristensen/ImageOptimizer/pull/46](https://github.com/madskristensen/ImageOptimizer/pull/46) .

Nous avons également des [exemples supplémentaires](https://github.com/microsoft/VSExtensibility/wiki/Samples#other-samples) à la fin de ce guide.

## <a name="step-1---modernize-the-project"></a>Étape 1 : moderniser le projet

Consultez [moderniser le projet](update-visual-studio-extension.md#modernize-your-vsix-project).

[e052465 de validation git](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e052465f30e6bed37e6d76eac016047095e8e18b)

Tout d’abord, nous prenons en relief le projet VSIX et le projet de test unitaire sur .NET 4.7.2 sous la page Propriétés des projets :

   ![Relief de version de l’infrastructure](media/samples/framework-bump.png)

L’optimiseur d’image a fait référence à des anciens packages 14. * et 15. * personnalisés. au lieu de cela, nous allons installer le [ `Microsoft.VisualStudio.Sdk` package NuGet](https://www.nuget.org/packages/microsoft.visualstudio.sdk) qui consolide toutes les références requises.

```Diff
-  <ItemGroup>
-    <PackageReference Include="Madskristensen.VisualStudio.SDK">
-      <Version>14.0.0-beta4</Version>
-    </PackageReference>
-    <PackageReference Include="Microsoft.VSSDK.BuildTools">
-      <Version>15.8.3247</Version>
-      <IncludeAssets>runtime; build; native; contentfiles; analyzers</IncludeAssets>
-      <PrivateAssets>all</PrivateAssets>
-    </PackageReference>
-  </ItemGroup>

+  <ItemGroup>
+    <PackageReference Include="Microsoft.VisualStudio.SDK">
+      <Version>16.9.31025.194</Version>
+    </PackageReference>
+  </ItemGroup>
```

La génération du projet s’effectue correctement et nous obtenons quelques avertissements de thread. Nous corrigeons ces avertissements en cliquant sur `ctrl` et `.` et en utilisant IntelliSense pour ajouter les lignes de basculement de thread manquantes.

## <a name="step-2---refactor-source-code-into-a-shared-project"></a>Étape 2 : refactorisation du code source en projet partagé

Consultez [projets partagés](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting).

La prise en charge de Visual Studio 2022 nécessite l’ajout d’un nouveau projet partagé qui contiendra le code source de l’extension qui sera partagé entre les projets VSIX Visual Studio 2019 et Visual Studio 2022.

1. Ajouter un nouveau projet partagé à votre solution

   [abf249d de validation git](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/abf249d5a4bed9010652f3f3fc4753c7c771c892)

   ![Ajouter un projet partagé](media/samples/add-shared-project.png)

1. Ajoutez une référence au projet partagé dans votre projet VSIX.

   [e8e941e de validation git](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/e8e941e5a5482cc15f5b9e7e4f1727f5cab5b12c)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Ajouter une référence de projet partagé" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Déplacez vos fichiers de code source (CS, XAML, resx) vers le nouveau projet partagé **, à l’exception** des éléments suivants :
    - `source.extension.vsixmanifest`
    - Fichiers de métadonnées d’extension (icônes, licences, notes de publication, etc.)
    - Fichiers VSCT
    - Fichiers liés
    - Bibliothèques ou outils externes qui doivent être inclus dans le VSIX

   [f31f051 de validation git](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/f31f0515305623988f2c355ed3bf5952fc8f1d9e)

   ![Déplacer des fichiers vers un projet partagé](media/samples/move-to-shared-project.png)

1. Déplacez maintenant toutes les métadonnées, les fichiers VSCT, les fichiers liés et les outils/bibliothèques externes vers un emplacement partagé et rajoutez-les en tant qu’éléments liés au projet VSIX. **Ne** supprimez pas `source.extension.vsixmanifest` .

   [73ba920 de validation git-déplacement de fichiers](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/73ba920b7db0bdb7c4d66aa9bc932c268efd49cb)

   [git commit d5e36b2-ajout d’outils/bibliothèques externes](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d5e36b2d047290d38ffc977511510bc03e257f13)

   1. Pour ce projet, nous devons déplacer l’icône d’extension, le fichier VSCT et les outils externes vers notre nouveau dossier `ImageOptimizer\Resources` . Copiez-les dans le dossier partagé et supprimez-les du projet VSIX.
   1. Ils sont de nouveau ajoutés en tant qu’éléments liés et si les éléments sont déjà liés, ils peuvent rester tels quels (licence par exemple).
   1. Vérifiez que l’action de génération et les autres propriétés sont définies correctement dans les fichiers liés ajoutés en les sélectionnant et en vérifiant la fenêtre de l’outil Propriétés. Pour notre projet, nous avons dû définir les éléments suivants :
       - Définir `icon.png` l’action de génération sur `Content` et marquer include dans VSIX sur `true`
       - Définir `ImageOptimizer.vsct` l’action de génération sur `VSCTComplile` et inclure dans VSIX dans `false`
       - Définissez toute l’action de génération des fichiers sous `Resources\Tools` à `Content` et marquée include dans VSIX à `true`

           ![Ajouter des fichiers liés au projet VSIX](media/samples/add-linked-files.png)

       - En outre, `ImageOptimizer.cs` est une dépendance de `ImageOptimizer.vsct` , pour cela, nous devons ajouter manuellement cette dépendance au fichier csproj :

          ```diff  
          - <Content Include="..\SharedFiles\ImageOptimizer.vsct">
          -   <Link>ImageOptimizer.vsct</Link>
          - </Content>
          - <Compile Include="..\SharedFiles\ImageOptimizer.cs">
          -   <Link>ImageOptimizer.cs</Link>
          - </Compile>

          + <VSCTCompile Include="..\SharedFiles\ImageOptimizer.vsct">
          +   <ResourceName>Menus.ctmenu</ResourceName>
          +   <Generator>VsctGenerator</Generator>
          +   <LastGenOutput>..\SharedFiles\ImageOptimizer.cs</LastGenOutput>
          + </VSCTCompile>
          + <Compile Include="..\SharedFiles\ImageOptimizer.cs">
          +   <AutoGen>True</AutoGen>
          +   <DesignTime>True</DesignTime>
          +   <DependentUpon>..\SharedFiles\ImageOptimizer.vsct</DependentUpon>
          + </Compile>
          ```

       - Si la fenêtre outil Propriétés vous empêche de définir une action de génération spécifique, vous pouvez modifier manuellement le csproj comme indiqué ci-dessus et définir l’action de génération si nécessaire.

1. Générez votre projet pour valider vos modifications et corriger les erreurs et les problèmes. Consultez la section [Forum aux questions](update-visual-studio-extension.md#q--a) pour les problèmes courants.

## <a name="step-3---add-a-visual-studio-2022-vsix-project"></a>Étape 3 : ajouter un projet VSIX Visual Studio 2022

Consultez [Ajouter la cible Visual Studio 2022](update-visual-studio-extension.md#add-a-visual-studio-2022-target).

1. Ajoutez un nouveau projet VSIX à votre solution.
1. Supprimez tout code source supplémentaire dans le nouveau projet, à l’exception de `source.extension.vsixmanifest.`

   ![Créer un projet VSIX](media/samples/visual-studio-2022-vsix-initial.png)

1. Ajoutez une référence à votre projet partagé.

   [dd49cb2 de validation git](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/dd49cb227b52c46206bf4be5c25790ac0377568d)

   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Ajouter une référence au projet partagé" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Ajoutez les fichiers liés de votre projet VSIX Visual Studio 2019 et vérifiez que leurs propriétés « action de génération » et « inclure dans VSIX » correspondent. Copiez également votre `source.extension.vsixmanifest` fichier, nous le modifierons ultérieurement pour prendre en charge Visual Studio 2022.

   [98c43ee de validation git](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/98c43ee6fbe912c38a1275542c44c65e11d7dbd9)

   ![Ajouter des fichiers liés au projet VSIX](media/samples/visual-studio-2022-add-linked-files.png)

1. Une tentative de génération indique qu’il manque une référence à `System.Windows.Forms` . Ajoutez-le simplement à notre projet Visual Studio 2022 et reconstruisez-le.

   [de71ccd de validation git](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/de71ccd9baff703aa6679392ad41a2cfe7bd7d72)

   ```Diff
   + <Reference Include="System.Windows.Forms" />
   ```

1. Mettez à niveau `Microsoft.VisualStudio.SDK` et `Microsoft.VSSDK.BuildTools` Empaquetez les références aux versions 2022 de Visual Studio.

   [d581fc3 de validation git](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/d581fc3c954974124dc7e31e5ecc85f78f7828ab)

   > [!NOTE]
   > Il s’agit des dernières versions disponibles lors de la création de ce guide. Il est recommandé de disposer des dernières versions disponibles.
   >
   > ```diff
   > -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
   > +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview-1-31216-1036" />
   > -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
   > +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-Visual Studio 2022-g3f11f5ab" />
   > ```

1. Modifiez votre `source.extension.vsixmanifest` fichier pour refléter le ciblage de Visual Studio 2022.

   [9d393c7 de validation git](https://github.com/madskristensen/ImageOptimizer/pull/46/commits/9d393c708c04ac4af48d1eb9ce3da4470db5d5cc)
   1. Définissez la `<InstallationTarget>` balise pour qu’elle reflète Visual Studio 2022 et indiquez une charge utile amd64 :

      ```xml
      <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
          <ProductArchitecture>amd64</ProductArchitecture>
      </InstallationTarget>
      ```

   1. Modifiez le composant requis pour inclure uniquement Visual Studio 2022 et versions ultérieures :

      ```Diff
      - <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,)" DisplayName="Visual Studio core editor" />
      + <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,)" DisplayName="Visual Studio core editor" />
      ```

Et c’est fini !

Avec cela, la génération génère désormais à la fois Visual Studio 2019 et Visual Studio 2022 VSIXes.

## <a name="other-samples"></a>Autres exemples

- [Outils PROPOWER](https://github.com/microsoft/VS-PPT/pull/244)
  - PeekF1
    - Permet d’obtenir des informations d’aide sur la classe ou l’objet sélectionné dans un navigateur Web.
  - FixMixedTabs
    - Analyse vos documents et remplace les tabulations par des espaces ou vice versa

## <a name="next-steps"></a>Étapes suivantes

Préparez la mise à jour de votre extension en lisant ce [Guide de début à fin](update-visual-studio-extension.md).
