---
title: Migrer un service de langue héritée (fr) Microsoft Docs
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
ms.openlocfilehash: 9e2eff3f3a27b7d8a276c8ed776c1e11d5ce332e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707114"
---
# <a name="migrating-a-legacy-language-service"></a>Migration d’un service de langage hérité
Vous pouvez migrer un service linguistique hérité vers une version ultérieure de Visual Studio en mettant à jour le projet et en ajoutant un fichier source.extension.vsixmanifest au projet. Le service linguistique lui-même continuera à fonctionner comme avant, parce que l’éditeur Visual Studio l’adapte.

 Les services linguistiques hérités sont mis en œuvre dans le cadre d’un VSPackage, mais la nouvelle façon de mettre en œuvre des fonctionnalités de service linguistique est d’utiliser des extensions MEF. Pour en savoir plus sur la nouvelle façon de mettre en œuvre un service linguistique, consultez [Editor et Language Service Extensions](../../extensibility/editor-and-language-service-extensions.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorera les performances de votre service linguistique et vous permettra de profiter des nouvelles fonctionnalités de l’éditeur.

## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migrer une solution de service de langue 2008 de Studio Visuel à une version ultérieure
 Les étapes suivantes montrent comment adapter un échantillon Visual Studio 2008 nommé RegExLanguageService. Vous pouvez trouver cet exemple dans une installation SDK Visual Studio 2008, dans le *parcours d’installation Visual Studio SDK*'VisualStudioIntegration’Samples’IDE’CSharp’Example.RegExLanguageServiceMD.

> [!IMPORTANT]
> Si votre service linguistique ne définit pas <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> `true` les couleurs, vous devez vous définir explicitement sur le VSPackage :

```
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]
```

#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Pour migrer un service de langue Visual Studio 2008 vers une version ultérieure

1. Installez les versions les plus nouvelles de Visual Studio et du Visual Studio SDK. Pour plus d’informations sur les moyens d’installer le SDK, voir [Installer le studio visuel SDK](../../extensibility/installing-the-visual-studio-sdk.md).

2. Modifier le fichier RegExLangServ.csproj (sans le charger dans Visual Studio.

     Dans `Import` le nœud qui se réfère au fichier Microsoft.VsSDK.targets, remplacez la valeur par le texte suivant.

    ```
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets
    ```

3. Enregistrer le fichier, puis le fermer.

4. Ouvrez la solution RegExLangServ.sln.

5. La fenêtre **de mise à niveau à sens unique** apparaît. Cliquez sur **OK**.

6. Mettre à jour les propriétés du projet. Ouvrez la fenêtre **Project Properties** en sélectionnant le nœud de projet dans le **Solution Explorer**, en cliquant à droite et en sélectionnant les **propriétés**.

    - Sur l’onglet **Application,** modifiez le **cadre cible** à **4.6.1**.

    - Sur l’onglet **Debug,** dans la boîte **de programme externe Démarrer,** tapez ** \<visual Studio chemin d’installation>'IDE-devenv.exe.**.

         Dans la **boîte d’arguments de ligne de commande,** type /**rootsuffix Exp**.

7. Mettre à jour les références suivantes :

    - Supprimer la référence à Microsoft.VisualStudio.Shell.9.0.dll, puis ajouter des références à Microsoft.VisualStudio.Shell.14.0.dll et Microsoft.VisualStudio.Shell.Immutable.11.0.dll.

    - Supprimer la référence à Microsoft.VisualStudio.Package.LanguageService.9.0.dll, puis ajouter une référence à Microsoft.VisualStudio.Package.LanguageService.14.0.dll.

    - Ajoutez une référence à Microsoft.VisualStudio.Shell.Interop.10.0.dll.

8. Ouvrez le fichier VsPkg.cs et modifiez la valeur de l’attribut `DefaultRegistryRoot`

    ```
    "Software\\Microsoft\\VisualStudio\\14.0Exp"
    ```

9. L’échantillon original n’enregistre pas son service linguistique, vous devez donc ajouter l’attribut suivant à VsPkg.cs.

    ```
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]
    ```

10. Vous devez ajouter un fichier source.extension.vsixmanifest.

    - Copiez ce fichier à partir d’une extension existante à votre répertoire de projet. (Une façon d’obtenir ce fichier est de créer un projet VSIX (sous **Fichier**, cliquez sur **Nouveau**, puis cliquez sur **Le projet**. Sous Visual Basic ou Cmd cliquez sur **Extensibility**, puis sélectionnez **VSIX Project**.)

    - Ajoutez le fichier à votre projet.

    - Dans les **propriétés**du fichier , **définissez Build Action** à **Aucun**.

    - Ouvrez le fichier avec le **VSIX Manifest Editor**.

    - Modifier les champs suivants :

    - **ID**: RegExLangServ

    - **Nom du produit**: RegExLangServ

    - **Description**: Un service de langue d’expression régulière.

    - Sous **Les actifs**, cliquez sur **Nouveau**, sélectionnez le **type** à **Microsoft.VisualStudio.VsPackage**, définissez la **source** à un projet dans la **solution actuelle**, puis définissez le **projet** à **RegExLangServ**.

    - Enregistrez et fermez le fichier.

11. Générez la solution. Les fichiers construits sont déployés à **%USERPROFILE% -AppData-Local-Microsoft-VisualStudio-14.0Exp-Extensions-MSIT’RegExLangServ\\**.

12. Démarrez le débogage. Une deuxième instance de Visual Studio a ouvert.

## <a name="see-also"></a>Voir aussi
- [Extensibilité du service de langage hérité](../../extensibility/internals/legacy-language-service-extensibility.md)
