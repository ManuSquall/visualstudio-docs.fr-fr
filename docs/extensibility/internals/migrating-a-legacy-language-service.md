---
title: Migration d’un Service de langage hérité | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, migrating
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 412b09016a3f889e0d6c5e40ff75895d5ae8ff48
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="migrating-a-legacy-language-service"></a>Migration d’un Service de langage hérité
Vous pouvez migrer un service de langage hérité vers une version ultérieure de Visual Studio en mise à jour le projet et en ajoutant un fichier source.extension.vsixmanifest au projet. Le service de langage lui-même continueront de fonctionner comme avant, car l’éditeur Visual Studio adapte.  
  
 Les services de langage hérité sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter des fonctionnalités de service de langage consiste à utiliser des extensions MEF. Pour plus d’informations sur la nouvelle façon d’implémenter un service de langage, consultez [éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## <a name="migrating-a-visual-studio-2008-language-service-solution-to-a-later-version"></a>Migration d’une Solution de Service de langage de Visual Studio 2008 vers une Version ultérieure  
 Les étapes suivantes montrent comment adapter un échantillon de Visual Studio 2008 nommé RegExLanguageService. Vous pouvez trouver cet exemple dans une installation de Visual Studio 2008 SDK, dans le *chemin d’installation de Visual Studio SDK*\VisualStudioIntegration\Samples\IDE\CSharp\Example.RegExLanguageService\ dossier.  
  
> [!IMPORTANT]
>  Si votre service de langage ne définit pas de couleurs, vous devez définir explicitement <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> à `true` sur le VSPackage :  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### <a name="to-migrate-a-visual-studio-2008-language-service-to-a-later-version"></a>Pour migrer un service de langage de Visual Studio 2008 vers une version ultérieure  
  
1.  Installez les versions plus récentes de Visual Studio et le Kit de développement logiciel Visual Studio. Pour plus d’informations sur les façons d’installer le SDK, consultez [l’installation de Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Modifier le fichier RegExLangServ.csproj (sans le chargeant dans Visual Studio.  
  
     Dans la `Import` nœud qui fait référence au fichier Microsoft.VsSDK.targets, remplacez la valeur par le texte suivant.  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  Enregistrez le fichier et fermez-le.  
  
4.  Ouvrez la solution RegExLangServ.sln.  
  
5.  Le **mise à niveau définitive** fenêtre s’affiche. Cliquez sur **OK**.  
  
6.  Mettre à jour les propriétés du projet. Ouvrez le **propriétés du projet** en sélectionnant le nœud du projet dans le **l’Explorateur de solutions**, avec le bouton droit, puis en sélectionnant **propriétés**.  
  
    -   Sur le **Application** , modifiez **framework cible** à **4.6.1**.  
  
    -   Sur le **déboguer** sous l’onglet du **démarrer le programme externe** , tapez  **\<chemin d’installation de Visual Studio > \Common7\IDE\devenv.exe.**.  
  
         Dans le **arguments de ligne de commande** , tapez /**rootsuffix Exp**.  
  
7.  Mettre à jour les références suivantes :  
  
    -   Supprimez la référence à Microsoft.VisualStudio.Shell.9.0.dll, puis ajouter des références à Microsoft.VisualStudio.Shell.14.0.dll et Microsoft.VisualStudio.Shell.Immutable.11.0.dll.  
  
    -   Supprimez la référence à Microsoft.VisualStudio.Package.LanguageService.9.0.dll, puis ajoutez une référence à Microsoft.VisualStudio.Package.LanguageService.14.0.dll.  
  
    -   Ajoutez une référence à Microsoft.VisualStudio.Shell.Interop.10.0.dll.  
  
8.  Ouvrez le fichier VsPkg.cs et modifiez la valeur de la `DefaultRegistryRoot` attribut  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. L’exemple d’origine n’enregistre pas son service de langage, vous devez donc ajouter l’attribut suivant à VsPkg.cs.  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. Vous devez ajouter un fichier source.extension.vsixmanifest.  
  
    -   Copiez ce fichier à partir d’une extension existante dans votre répertoire de projet. (Une pour obtenir ce fichier consiste à créer un projet VSIX (sous **fichier**, cliquez sur **nouveau**, puis cliquez sur **projet**. Cliquez sur sous Visual Basic ou c# **extensibilité**, puis sélectionnez **projet VSIX**.)  
  
    -   Ajoutez le fichier à votre projet.  
  
    -   Dans du fichier **propriétés**, définissez **Action de génération** à **aucun**.  
  
    -   Ouvrez le fichier avec le **éditeur de manifeste VSIX**.  
  
    -   Modifier les champs suivants :  
  
    -   **ID**: RegExLangServ  
  
    -   **Nom de produit**: RegExLangServ  
  
    -   **Description**: un service de langage d’expression régulière.  
  
    -   Sous **actifs**, cliquez sur **nouveau**, sélectionnez le **Type** à **Microsoft.VisualStudio.VsPackage**, définissez le **Source** à **un projet dans la solution actuelle**, puis définissez le **projet** à **RegExLangServ**.  
  
    -   Enregistrez et fermez le fichier.  
  
11. Générez la solution. Les fichiers générés sont déployées sur **%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\14.0Exp\Extensions\MSIT\ RegExLangServ\\**.  
  
12. Démarrez le débogage. Une deuxième instance de Visual Studio ouvert.  
  
## <a name="see-also"></a>Voir aussi  
 [Extensibilité du service de langage hérité](../../extensibility/internals/legacy-language-service-extensibility.md)