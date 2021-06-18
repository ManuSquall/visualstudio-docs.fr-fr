---
title: Mettre à jour une extension Visual Studio
description: Découvrez comment mettre à jour votre extension Visual Studio pour qu’elle fonctionne avec Visual Studio 2022.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 514c9654a741e4e1e565f0cb2becdbe3157fab0c
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308738"
---
# <a name="update-a-visual-studio-extension-for-visual-studio-2022"></a>Mettre à jour une extension Visual Studio pour Visual Studio 2022

Vous pouvez mettre à jour votre extension de façon à ce qu’elle fonctionne avec Visual Studio 2022 Preview en suivant ce guide. Visual Studio 2022 Preview est une application 64 bits et présente des modifications avec rupture dans le kit de développement logiciel (SDK) VS. Ce guide vous guide tout au long des étapes requises pour faire fonctionner votre extension avec la version préliminaire actuelle de Visual Studio 2022. votre extension peut donc être prête à être installée par les utilisateurs avant que Visual Studio 2022 n’atteigne la disponibilité générale.

## <a name="installing"></a>En cours d'installation

Installez Visual Studio 2022 Preview dans [Visual studio 2022 Preview downloads](https://visualstudio.microsoft.com/vs/preview/vs2022)(en anglais).

### <a name="extensions-written-in-a-net-language"></a>Extensions écrites dans un langage .NET

Le kit de développement logiciel VS SDK ciblant Visual Studio 2022 pour les extensions managées est *exclusivement réservé* à NuGet :

- Le méta-package [Microsoft. VisualStudio. SDK](https://www.nuget.org/packages/Microsoft.VisualStudio.Sdk/) (17. x versions) apporte la plupart ou la totalité des assemblys de référence dont vous aurez besoin.
- Le package [Microsoft. VSSDK. BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools/) (17. x versions) doit être référencé à partir de votre projet VSIX afin de pouvoir générer un VSIX compatible avec Visual Studio 2022.

Les extensions *doivent* être compilées avec la plateforme « Any CPU » ou « x64 ». La plateforme « x86 » est incompatible avec le processus 64 bits de Visual Studio 2022.

### <a name="extensions-written-in-c"></a>Extensions écrites en C++

Le SDK VS pour les extensions compilées avec C++ est disponible avec le kit de développement logiciel (SDK) Visual Studio installé, comme d’habitude.

Les extensions *doivent* être compilées spécifiquement avec le kit de développement logiciel (SDK) Visual Studio 2022 et pour amd64.

### <a name="update-your-extension-to-visual-studio-2022"></a>Mettre à jour votre extension vers Visual Studio 2022

#### <a name="extensions-with-running-code"></a>Extensions avec code en cours d’exécution

Les extensions avec du code en cours d’exécution *doivent* être compilées spécifiquement pour Visual Studio 2022. Visual Studio 2022 ne chargera pas les extensions qui ne ciblent pas spécifiquement Visual Studio 2022.

Découvrez comment migrer vos extensions 2022 antérieures à Visual Studio vers Visual Studio 2022 :

1. [Moderniser vos projets](#modernize-your-vsix-project).
1. [Refactorisez votre code source dans un projet partagé](#use-shared-projects-for-multi-targeting) pour permettre le ciblage de Visual Studio 2022 et des versions antérieures.
1. [Ajoutez un projet VSIX ciblé par Visual Studio 2022](#add-a-visual-studio-2022-target)et notre [table de remappage de package/assembly](migrated-assemblies.md).
1. [Effectuer les ajustements de code nécessaires](#handle-breaking-api-changes).
1. [Test de votre extension Visual Studio 2022](#test-your-extension).
1. [Publication de votre extension Visual Studio 2022](#publish-your-extension).

#### <a name="extensions-without-running-code"></a>Extensions sans exécuter de code

Les extensions qui ne contiennent pas de code en cours d’exécution (par exemple, les modèles de projet/élément) ne sont *pas* requises pour suivre les étapes ci-dessus, y compris la production de deux VSIXs distincts.

Au lieu de cela, le VSIX doit être modifié de sorte que son `source.extension.vsixmanifest` fichier déclare deux cibles d’installation, comme suit :

```xml
<Installation>
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0,17.0)">
      <ProductArchitecture>x86</ProductArchitecture>
   </InstallationTarget>
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
</Installation>
```

Vous pouvez ignorer les étapes de cet article sur l’utilisation de projets partagés et de plusieurs VSIXs. Vous pouvez procéder à des [tests](#test-your-extension)!

> [!NOTE]
> Si vous créez une *nouvelle* extension Visual Studio à l’aide de visual studio 2022 Preview et que vous souhaitez (également) cibler visual studio 2019 ou une version antérieure, consultez [ce guide](target-previous-versions.md).

### <a name="msbuild-tasks"></a>tâches MSBuild

Si vous créez des tâches MSBuild, sachez que dans Visual Studio 2022 il est bien plus probable qu’elles soient chargées dans un processus de MSBuild.exe 64 bits. Si votre tâche nécessite l’exécution d’un processus 32 bits, reportez-vous à [cette documentation MSBuild](../../msbuild/how-to-configure-targets-and-tasks.md#usingtask-attributes-and-task-parameters) pour vérifier que MSBuild sait charger votre tâche dans un processus 32 bits.

## <a name="modernize-your-vsix-project"></a>Moderniser votre projet VSIX

Avant d’ajouter la prise en charge de Visual Studio 2022 à votre extension, nous vous recommandons vivement de prendre le temps de nettoyer et de moderniser votre projet existant avant d’aller plus loin, notamment :

1. [Migrez de packages.config `PackageReference` à ](/nuget/consume-packages/migrate-packages-config-to-package-reference).

1. Remplacez toutes les références d’assembly du kit de développement logiciel (SDK) par des éléments PackageReference.

   ```diff
   -<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   +<PackageReference Include="Microsoft.VisualStudio.OLE.Interop" Version="..." />
   ```

   > [!TIP]
   > Vous pouvez remplacer de *nombreuses* références d’assembly par *un* seul PackageReference dans notre offre :
   >
   >```diff
   >-<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop.8.0" />
   >+<PackageReference Include="Microsoft.VisualStudio.Sdk" >Version="..." />
   >```

   Veillez à sélectionner les versions de package qui correspondent à la version minimale de Visual Studio que vous ciblez.

   Certains assemblys qui ne sont pas propres au kit de développement logiciel (SDK) VS (par exemple, Newtonsoft.Json.dll) peuvent avoir été détectables via une `<Reference Include="Newtonsoft.Json" />` référence simple avant Visual studio 2022, mais dans Visual studio 2022 requiert une référence de package à la place, car dans Visual studio 2022, nous supprimons certains répertoires du runtime et du SDK Visual Studio du chemin de recherche des assemblys par défaut de MSBuild

   Lors du basculement des références d’assembly direct vers les références de package NuGet, vous pouvez récupérer des références d’assembly supplémentaires et des packages d’analyseurs en raison de l’installation automatique par NuGet de la fermeture transitive des dépendances. C’est généralement le cas, mais des avertissements supplémentaires peuvent être signalés pendant votre génération. Parcourez ces avertissements et résolvez-en autant que possible, et supprimez les avertissements que vous ne pouvez pas résoudre à l’aide de régions dans le code `#pragma warning disable <id>` .

## <a name="use-shared-projects-for-multi-targeting"></a>Utiliser des projets partagés pour le multi-ciblage

Les [projets partagés](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) sont un type de projet qui a été introduit dans Visual Studio 2015. Les projets partagés dans Visual Studio permettent aux fichiers de code source d’être partagés entre plusieurs projets et de générer différemment à l’aide de symboles de compilation conditionnelle et de jeux de références uniques.

Étant donné que Visual Studio 2022 requiert un ensemble distinct d’assemblys de référence provenant de toutes les versions antérieures de Visual Studio, nous vous aiderons à utiliser des projets partagés pour cibler facilement votre extension vers les versions antérieures à Visual Studio 2022 et Visual Studio 2022 (et versions ultérieures), en vous donnant un partage de code, mais des références distinctes.

Dans le contexte des extensions Visual Studio, vous pouvez avoir un projet VSIX pour Visual Studio 2022 et versions ultérieures et un projet VSIX pour Visual Studio 2019 et versions antérieures. Chacun de ces projets contient uniquement un `source.extension.vsixmanifest` et les références du package au kit de développement logiciel (SDK) 16. x ou au kit de développement logiciel (SDK) 17. x. Ces projets VSIX auraient également une référence de projet partagée à un nouveau projet partagé qui hébergera tout votre code source qui peut être partagé entre les deux versions de VS.

Comme point de départ, pour ce document, nous partons du principe que vous disposez déjà d’un projet VSIX ciblant Visual Studio 2019 et que vous souhaitez que votre extension fonctionne sur Visual Studio 2022.

Toutes ces étapes peuvent être effectuées avec Visual Studio 2019.

1. Si vous ne l’avez pas encore fait, [Modernisez vos projets](#modernize-your-vsix-project) pour faciliter les étapes ultérieures dans le processus de mise à jour.

1. Ajoutez un nouveau projet partagé à votre solution pour chaque projet existant qui fait référence au kit de développement logiciel (SDK) VS.
   ![Ajouter un nouveau projet, commande ](media/update-visual-studio-extension/add-new-project.png)
    ![ nouveau modèle de projet](media/update-visual-studio-extension/new-shared-project-template.png)

1. Ajoutez une référence de chaque projet référençant le kit de développement logiciel VS SDK à son équivalent de projet partagé.
   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Ajouter une référence de projet partagé" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Déplacez tout le code source (y compris. cs,. resx) à partir de chaque projet de référence du kit de développement logiciel (SDK) VS vers son équivalent de projet partagé.
Laissez le `source.extension.vsixmanifest` fichier dans le projet VSIX.
   ![Le projet partagé contient tous les fichiers sources](media/update-visual-studio-extension/source-files-in-shared-project.png)

1. Les fichiers de métadonnées (notes de publication, licence, icônes, etc.) et les fichiers VSCT doivent être déplacés vers un répertoire partagé et ajoutés en tant que fichiers liés au projet VSIX.
   ![Ajouter des métadonnées et des fichiers VSCT en tant que fichiers liés](media/update-visual-studio-extension/add-linked-items-to-vsix.png)
    - Pour les fichiers de métadonnées, affectez à BuildAction la valeur `Content` et affectez à include dans VSIX la valeur `true` .

      ![Inclure des fichiers de métadonnées dans VSIX](./media/update-visual-studio-extension/include-metadata-files-in-vsix.png)
    - Pour les fichiers VSCT, affectez à BuildAction la valeur `VSCTCompile` et n’incluez pas dans VSIX.
      Visual Studio peut se plaindre que ce paramètre n’est pas pris en charge, mais vous pouvez modifier manuellement l’action de génération en déchargeant le projet et `Content` en remplaçant par `VSCTCompile`

    ```diff
    -<Content Include="..\SharedFiles\VSIXProject1Package.vsct">
    -  <Link>VSIXProject1Package.vsct</Link>
    -</Content>
    +<VSCTCompile Include="..\SharedFiles\VSIXProject1Package.vsct">
    +  <Link>VSIXProject1Package.vsct</Link>
    +  <ResourceName>Menus.ctmenu</ResourceName>
    +</VSCTCompile>
    ```

      ![Définir les fichiers VSCT en tant que VSCTCompile](media/update-visual-studio-extension/build-linked-vsct-files.png)

1. Générez votre ou vos projets pour confirmer que vous n’avez pas introduit de nouvelles erreurs.

Votre projet est maintenant prêt à ajouter la prise en charge de Visual Studio 2022.

## <a name="add-a-visual-studio-2022-target"></a>Ajouter une cible Visual Studio 2022

Ce document part du principe que vous avez effectué les étapes nécessaires pour [factoriser votre extension Visual Studio avec des projets partagés](#use-shared-projects-for-multi-targeting).

Pour ajouter la prise en charge de Visual Studio 2022 à votre extension, procédez comme suit, ce qui peut être effectué à l’aide de Visual Studio 2019 :

1. Ajoutez un nouveau projet VSIX à votre solution. Il s’agit du projet qui cible Visual Studio 2022. Supprimez le code source fourni avec le modèle, mais *conservez le `source.extension.vsixmanifest` fichier*.

1. Sur votre nouveau projet VSIX, ajoutez une référence de projet partagé au même projet partagé que vos références VSIX ciblant Visual Studio 2019.

   ![Une solution avec un projet partagé et deux projets VSIX](media/update-visual-studio-extension/shared-project-with-two-heads.png)

1. Vérifiez que le nouveau projet VSIX est correctement généré. Vous devrez peut-être ajouter des références pour qu’elles correspondent à votre projet VSIX d’origine afin de résoudre les erreurs de compilateur.

1. Pour les extensions VS managées, mettez à jour vos références de package de 16. x (ou version antérieure) vers les versions de package 17. x dans votre fichier projet ciblé Visual Studio 2022 à l’aide du gestionnaire de package NuGet ou en modifiant directement le fichier projet :

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    ```

   Vous utiliserez les versions qui sont réellement disponibles à partir de nuget.org. Ceux utilisés précédemment ne sont qu’à des fins de démonstration.

   Dans de nombreux cas, les ID de package ont changé. Pour obtenir la liste des modifications dans Visual Studio 2022, reportez-vous à la [table de mappage de package/assembly](migrated-assemblies.md) .

   Les extensions écrites en C++ ne disposent pas encore d’un kit de développement logiciel (SDK) disponible pour la compilation.

1. Pour les projets C++, ils doivent être compilés pour amd64. Pour les extensions managées, envisagez de modifier votre projet de façon à ce qu’il n’y ait plus d’UC à cibler `x64` , afin de refléter cela dans Visual Studio 2022, votre extension se charge toujours dans un processus 64 bits. `Any CPU` C’est également parfait, mais peut générer des avertissements si vous référencez des binaires natifs x64 uniquement.

   Toute dépendance que votre extension peut avoir sur un module natif doit être mise à jour d’une image x86 vers une image amd64.

1. Modifiez votre `source.extension.vsixmanifest` fichier pour refléter le ciblage de Visual Studio 2022. Définissez la `<InstallationTarget>` balise pour qu’elle reflète Visual Studio 2022 et indiquez une charge utile amd64 :

   ```xml
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
   ```

   Dans Visual Studio 2019, le concepteur de ce fichier n’expose pas le nouvel `ProductArchitecture` élément. cette modification devra donc être effectuée à l’aide d’un éditeur XML, auquel vous pouvez accéder via la commande **Ouvrir avec** dans **Explorateur de solutions**.

   Cet `ProductArchitecture` élément est critique. Visual Studio 2022 n’installe *pas* votre extension sans celui-ci.

   | Élément | Valeur | Description |
   | - | - | - |
   | ProductArchitecture | X86, AMD64 | Plateformes prises en charge par cette extension VSIX. Ne respecte pas la casse. Une plateforme par élément et un élément par InstallTarget. Pour les versions de produit inférieures à 17,0, la valeur par défaut est x86 et peut être omise.  Pour les versions de produit 17,0 et ultérieures, cet élément est obligatoire et il n’y a pas de valeur par défaut. Pour Visual Studio 2022, le seul contenu valide pour cet élément est « amd64 ». |

1. Effectuez les autres ajustements nécessaires dans votre source. extension. vsixmanifest pour qu’il corresponde à celui qui cible Visual Studio 2019 (le cas échéant). Il est essentiel que l’ID de l’extension VSIX, dans l' `Identity` élément du manifeste, soit identique pour les deux extensions.

À ce stade, vous disposez d’une extension ciblée Visual Studio 2022. Vous devez générer votre projet VSIX ciblé par Visual Studio 2022 et [utiliser les arrêts de build qui s’affichent](#handle-breaking-api-changes). Si vous n’avez pas des arrêts de build dans votre projet VSIX ciblé par Visual Studio 2022, félicitations : vous êtes prêt à effectuer des tests !

## <a name="handle-breaking-api-changes"></a>Gérer les modifications de l’API avec rupture

Il existe des [modifications d’API](breaking-api-list.md) dans Visual Studio 2022 qui peuvent nécessiter des modifications de votre code lorsque celles-ci sont exécutées sur des versions antérieures. Consultez ce document pour obtenir des conseils sur la façon de mettre à jour votre code pour chacun d’entre eux.

Lorsque vous adaptez votre code, nous vous recommandons d’utiliser la [compilation conditionnelle](#use-conditional-compilation-symbols) afin que votre code puisse continuer à prendre en charge les versions antérieures à visual studio 2022 tout en ajoutant la prise en charge de visual studio 2022.

Lorsque vous créez votre extension ciblée Visual Studio 2022, passez au [test](#test-your-extension).

## <a name="use-conditional-compilation-symbols"></a>Utiliser des symboles de compilation conditionnelle

Si vous souhaitez utiliser le même code source, même le même fichier, pour Visual Studio 2022 et les versions antérieures, vous devrez peut-être utiliser la compilation conditionnelle afin de pouvoir embrancher votre code pour s’adapter aux modifications avec rupture. La compilation conditionnelle est une fonctionnalité des langages C#, Visual Basic et C++ qui peut être utilisée pour partager la plus grande partie du code tout en prenant en accueillir des API divergentes dans des emplacements spécifiques.

Vous trouverez plus d’informations sur l’utilisation des directives de préprocesseur et des symboles de compilation conditionnelle dans la [directive de préprocesseur #if](/dotnet/csharp/language-reference/preprocessor-directives#conditional-compilation)Microsoft docs.

Le ou les projets qui ciblent des versions antérieures de Visual Studio auront besoin d’un symbole de compilation conditionnelle qui peut ensuite être utilisé pour dupliquer le code afin d’utiliser les différentes API. Vous pouvez définir le symbole de compilation conditionnelle dans la page de propriétés du projet, comme illustré dans l’image suivante :

![Définition des symboles de compilation conditionnelle](media/update-visual-studio-extension/conditional-compilation-symbols.png)

Veillez à définir le symbole de compilation pour *toutes les* configurations, car par défaut, le symbole que vous entrez ne peut s’appliquer qu’à une seule configuration.

### <a name="c-techniques"></a>\#Techniques C

Vous pouvez ensuite utiliser ce symbole comme directive de préprocesseur ( `#if` ), comme illustré dans le code suivant. Vous pouvez ensuite répartir votre code pour gérer la modification avec rupture entre les différentes versions de Visual Studio.

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
#if Visual Studio 2019
    shell.LoadUILibrary(myGuid, myFlags, out uint ptrLib);
#else
    shell.LoadUILibrary(myGuid, myFlags, out IntPtr ptrLib);
#endif
```

Dans certains cas, vous pouvez simplement utiliser `var` pour éviter d’attribuer un nom au type, évitant ainsi le besoin de `#if` régions. L’extrait de code ci-dessus peut également être écrit comme suit :

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
    shell.LoadUILibrary(myGuid, myFlags, out var ptrLib);
```

Lorsque vous utilisez la `#if` syntaxe, Notez comment vous pouvez utiliser la liste déroulante du contexte du service de langage dans le document présenté ci-dessous pour modifier la mise en surbrillance de la syntaxe et l’autre aide que le service de langage offre pour attirer l’attention sur une version cible de Visual Studio pour notre extension par rapport à une autre.

![Compilation conditionnelle dans un projet partagé](media/update-visual-studio-extension/conditional-compilation-if-region.png)

### <a name="xaml-sharing-techniques"></a>Techniques de partage XAML

XAML n’a pas de préprocesseur pour permettre la personnalisation du contenu basé sur les symboles de préprocesseur. La copie et la gestion de deux pages XAML où leur contenu doit différer entre Visual Studio 2022 et des versions antérieures peuvent être nécessaires.

Toutefois, dans certains cas, une référence à un type qui existe dans des assemblys distincts dans Visual Studio 2022 et des versions antérieures peut toujours être représentée dans un fichier XAML en supprimant l’espace de noms qui référence l’assembly :

```diff
-xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
-Value="{DynamicResource {x:Static vsui:TreeViewColors.SelectedItemActiveBrushKey}}"
+Value="{DynamicResource TreeViewColors.SelectedItemActiveBrushKey}"
```

## <a name="test-your-extension"></a>Tester votre extension

Pour tester une extension qui cible Visual Studio 2022, vous devez avoir installé Visual Studio 2022 preview.
Vous ne serez pas en mesure d’exécuter des extensions 64 bits sur les versions de Visual Studio antérieures à Visual Studio 2022 preview.

Vous pouvez utiliser Visual Studio 2022 Preview pour générer et tester vos extensions, qu’elles ciblent Visual Studio 2022 ou une version antérieure. Lors du lancement d’un projet VSIX à partir de Visual Studio 2022, une instance expérimentale de Visual Studio est lancée.

Nous vous recommandons vivement de tester chaque version de Visual Studio que vous prévoyez de prendre en charge par l’extension.

Vous êtes maintenant prêt à [publier votre extension](#publish-your-extension).

## <a name="publish-your-extension"></a>Publier votre extension

Très bien, vous avez ajouté une cible Visual Studio 2022 à votre extension et vous l’avez testée. Vous êtes maintenant prêt à publier l’extension pour le monde.

### <a name="visual-studio-marketplace"></a>Visual Studio Marketplace

La publication de votre extension sur le [Visual Studio Marketplace](https://marketplace.visualstudio.com/) est un excellent moyen de faire en sorte que les nouveaux utilisateurs recherchent et installent votre extension. Que votre extension cible uniquement Visual Studio 2022 ou cible les versions antérieures de Visual Studio, la place de marché est là pour vous prendre en charge.

À l’avenir, la place de marché vous permettra de télécharger plusieurs VSIXs dans une seule liste de places de marché, ce qui vous permet de télécharger votre extension VSIX ciblée Visual Studio 2022 et un VSIX antérieur à Visual Studio 2022. Vos utilisateurs obtiendront automatiquement le VSIX adapté à la version Visual Studio qu’ils ont installée, lors de l’utilisation du gestionnaire d’extensions VS.

Pour les versions préliminaires de Visual Studio 2022, la place de marché ne prend en charge qu’un seul fichier VSIX par liste de la place de marché. Alors que Visual Studio 2022 est en version préliminaire, nous vous encourageons à disposer d’une liste distincte de la place de marché Visual Studio 2022 uniquement pour votre extension. De cette façon, vous pouvez itérer votre extension Visual Studio 2022 en fonction des besoins sans affecter vos clients sur les versions antérieures de Visual Studio. Vous pouvez également marquer l’extension comme « Preview » pour définir l’attente. elle sera probablement moins fiable, même si la source de cette non-fiabilité est Visual Studio 2022, par rapport à votre extension de grand public.

### <a name="custom-installer"></a>Programme d’installation personnalisé

Si vous générez un fichier MSI/EXE pour installer votre extension et générer vsixinstaller.exe pour installer (partie de) votre extension, sachez que le programme d’installation VSIX dans Visual Studio 2022 a été mis à jour. Les développeurs doivent utiliser la version du programme d’installation VSIX qui est fournie avec Visual Studio 2022 pour installer des extensions à Visual Studio 2022. Dans Visual Studio 2022, le programme d’installation VSIX installe également les extensions applicables ciblant les versions antérieures de Visual Studio installées côte à côte avec Visual Studio 2022 sur le même ordinateur.

### <a name="network-share"></a>Partage réseau

Vous pouvez partager votre extension sur un réseau local ou tout autre moyen. Si vous ciblez Visual Studio 2022 et pré-Visual Studio 2022, vous devez vous partager plusieurs VSIXs individuellement et leur attribuer des noms de fichiers (ou les placer dans des dossiers uniques) qui aident les utilisateurs à identifier le VSIX à installer en fonction de la version de Visual Studio qu’ils ont installée.

### <a name="other-considerations"></a>Autres considérations

#### <a name="dependencies"></a>Dépendances

Si votre extension VSIX spécifie un autre VSIX en tant que dépendance par le biais de l' `<dependency>` élément, chaque extension VSIX référencée doit être installée dans les mêmes cibles et architectures de produit que votre extension VSIX. Si un VSIX dépendant ne prend pas en charge l’installation ciblée de Visual Studio, votre extension VSIX échoue. Il est OK que le VSIX dépendant prenne en charge plus de cibles et d’architectures que la vôtre, juste au moins. Cette restriction signifie que l’approche de déploiement et de distribution d’un VSIX avec des dépendances doit refléter celle de leurs dépendants.

## <a name="q--a"></a>Questions et réponses

**Q**: mon extension ne nécessite pas de modification de l’interopérabilité, car elle fournit uniquement des données (par exemple, des modèles), puis-je créer une extension unique qui inclut également Visual Studio 2022 ?

**R** : Oui.  Pour plus d’informations à ce sujet, consultez [Extensions sans exécuter de code](#extensions-without-running-code) .

**Q**: une dépendance NuGet est apportée dans les anciens assemblys d’interopérabilité et provoquant des conflits de classes.

**R**: ajoutez la ligne suivante à votre fichier. csproj pour éviter les doublons d’assemblys :

```xml
    <PackageReference Include="<Name of offending assembly>" ExcludeAssets="compile" PrivateAssets="all" />
```

Cela empêchera les références de package d’importer l’ancienne version de l’assembly à partir d’autres dépendances.

**Q**: mes commandes et raccourcis clavier ne fonctionnent pas dans Visual Studio après avoir basculé mes fichiers sources vers un projet partagé.

**R**: l' [étape 2,4](samples.md#step-2---refactor-source-code-into-a-shared-project) de l’exemple d’optimiseur d’image montre comment ajouter des fichiers vsct en tant qu’éléments liés afin qu’ils soient compilés dans votre fichier vsct.

## <a name="next-steps"></a>Étapes suivantes

Suivez un exemple pas à pas, [ImageOptimizer](samples.md), avec des liens vers le projet et des modifications de code pour chaque étape.
