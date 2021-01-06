---
title: Migration d’un service de langage hérité | Microsoft Docs
description: Apprenez à mettre à jour un service de langage avec la dernière version de Visual Studio en mettant à jour le projet et en ajoutant un fichier source. extension. vsixmanifest.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ced200ff24b17f312e63642c8083f038a6fc6a4d
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877830"
---
# <a name="migrating-a-legacy-language-service"></a>Migration d’un service de langage hérité
Vous pouvez migrer un service de langage hérité vers une version ultérieure de Visual Studio en mettant à jour le projet et en ajoutant un fichier. extension. vsixmanifest source au projet. Le service de langage lui-même continue à fonctionner comme avant, car l’éditeur Visual Studio l’adapte.

 Les services de langage hérités sont implémentés dans le cadre d’un VSPackage, mais la meilleure façon d’implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter un service de langage, consultez [éditeur et extensions du service de langage](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser la nouvelle API Editor dès que possible. Cela améliore les performances de votre service de langage et vous permet de tirer parti des nouvelles fonctionnalités de l’éditeur.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migration d’une solution de service de langage Visual Studio 2008 vers une version ultérieure
 Les étapes suivantes montrent comment adapter un exemple Visual Studio 2008 nommé RegExLanguageService. Vous pouvez trouver cet exemple dans une installation du kit de développement logiciel (SDK) Visual Studio 2008, dans le dossier \VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ *chemin d’installation du kit de développement logiciel Visual Studio*.

> [!IMPORTANT]
> Si votre service de langage ne définit pas de couleurs, vous devez définir explicitement <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> `true` sur sur le VSPackage :

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Pour migrer un service de langage Visual Studio 2008 vers une version ultérieure

1. Installez les versions plus récentes de Visual Studio et du kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations sur les méthodes d’installation du kit de développement logiciel (SDK), consultez [installation du kit de développement logiciel Visual Studio](../../extensibility/installing-the-visual-studio-sdk.md).

2. Modifiez le fichier RegExLangServ. csproj (sans le charger dans Visual Studio).

     Dans le `Import` nœud qui fait référence au fichier Microsoft. VsSDK. targets, remplacez la valeur par le texte suivant.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Enregistrez le fichier, puis fermez-le.

4. Ouvrez la solution RegExLangServ. sln.

5. La fenêtre de **mise à niveau à sens unique** s’affiche. Cliquez sur **OK**.

6. Mettez à jour les propriétés du projet. Ouvrez la fenêtre **Propriétés du projet** en sélectionnant le nœud du projet dans la **Explorateur de solutions**, en cliquant avec le bouton droit et en sélectionnant **Propriétés**.

    - Sous l’onglet **application** , remplacez la version **cible de .NET Framework** par **4.6.1**.

    - Sous l’onglet **Déboguer** , dans la zone **Démarrer le programme externe** , tapez **\<Visual Studio installation path>\Common7\IDE\devenv.exe.**.

         Dans la zone **arguments de ligne de commande** , tapez/**rootsuffix exp**.

7. Mettez à jour les références suivantes :

    - Supprimez la référence à Microsoft.VisualStudio.Shell.9.0.dll, puis ajoutez des références à Microsoft.VisualStudio.Shell.14.0.dll et Microsoft.VisualStudio.Shell.Immutable.11.0.dll.

    - Supprimez la référence à Microsoft.VisualStudio.Package.LanguageService.9.0.dll, puis ajoutez une référence à Microsoft.VisualStudio.Package.LanguageService.14.0.dll.

    - Ajoutez une référence à Microsoft.VisualStudio.Shell.Interop.10.0.dll.

8. Ouvrez le fichier VsPkg.cs et remplacez la valeur de l' `DefaultRegistryRoot` attribut par

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. L’exemple d’origine n’inscrit pas son service de langage. vous devez donc ajouter l’attribut suivant à VsPkg.cs.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. Vous devez ajouter un fichier source. extension. vsixmanifest.

    - Copiez ce fichier à partir d’une extension existante dans le répertoire de votre projet. (Pour obtenir ce fichier, vous pouvez créer un projet VSIX (sous **fichier**, cliquez sur **nouveau**, puis sur **projet**. Sous Visual Basic ou C#, cliquez sur **extensibilité**, puis sélectionnez **projet VSIX**.)

    - Ajoutez le fichier à votre projet.

    - Dans les **Propriétés** du fichier, affectez à **action de génération** la valeur **aucun**.

    - Ouvrez le fichier avec l' **éditeur de manifeste VSIX**.

    - Modifiez les champs suivants :

    - **ID**: RegExLangServ

    - **Nom du produit**: RegExLangServ

    - **Description**: service de langage d’expression régulière.

    - Sous **composants**, cliquez **sur nouveau**, sélectionnez **le type** de **Microsoft. VisualStudio. VSPackage**, définissez la **source** sur **un projet dans la solution actuelle**, puis définissez le **projet** sur **RegExLangServ**.

    - Enregistrez et fermez le fichier.

11. Générez la solution. Les fichiers générés sont déployés sur **%UserProfile%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ \\**.

12. Démarrez le débogage. Une deuxième instance de Visual Studio A été ouverte.

## <a name="see-also"></a>Voir aussi
- [Extensibilité du service de langage hérité](../../extensibility/internals/legacy-language-service-extensibility.md)
