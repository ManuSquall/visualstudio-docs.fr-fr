---
title: "Migration d’un Service de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "migration des services de langage"
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Migration d’un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Vous pouvez migrer un service de langage hérité vers une version ultérieure de Visual Studio en mettant à jour le projet et en ajoutant un fichier source.extension.vsixmanifest au projet. Le service de langage lui\-même continueront à fonctionner comme avant, car l’éditeur Visual Studio adapte.  
  
 Les services de langage ancien sont implémentés en tant que partie d’un VSPackage, mais la plus récente pour implémenter les fonctionnalités du service de langage consiste à utiliser les extensions MEF. Pour en savoir plus sur la nouvelle façon d’implémenter un service de langage, consultez [Éditeur et les Extensions de Service de langage](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Nous vous recommandons de commencer à utiliser l’API de l’éditeur de nouveau dès que possible. Cela améliorer les performances de votre service de langage et vous permettent de tirer parti des nouvelles fonctionnalités de l’éditeur.  
  
## Migration d’une Solution de Service de langage de Visual Studio 2008 vers une Version ultérieure  
 Les étapes suivantes montrent comment adapter un exemple Visual Studio 2008 nommé RegExLanguageService. Vous trouverez cet exemple dans une installation du SDK de Visual Studio 2008, dans le *chemin d’installation de Visual Studio SDK*\\VisualStudioIntegration\\Samples\\IDE\\CSharp\\Example.RegExLanguageService\\ dossier.  
  
> [!IMPORTANT]
>  Si votre service de langage ne définit pas de couleurs, vous devez définir explicitement <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> à `true` sur le package VS :  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### Pour migrer un service de langage de Visual Studio 2008 vers une version ultérieure  
  
1.  Installez les versions plus récentes de Visual Studio et le Kit de développement Visual Studio. Pour plus d’informations sur les façons d’installer le Kit de développement, consultez [L'installation du Kit de développement logiciel de Visual Studio](../../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Modifier le fichier RegExLangServ.csproj \(sans le charger dans Visual Studio.  
  
     Dans la `Import` nœud qui fait référence au fichier Microsoft.VsSDK.targets, remplacez la valeur par le texte suivant.  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  Enregistrez le fichier et fermez\-le.  
  
4.  Ouvrez la solution RegExLangServ.sln.  
  
5.  Le **mise à niveau définitive** fenêtre s’affiche. Cliquez sur **OK**.  
  
6.  Mettre à jour les propriétés du projet. Ouvrez le **Propriétés du projet** en sélectionnant le nœud du projet dans le **l’Explorateur de solutions**, avec le bouton droit, puis en sélectionnant **propriétés**.  
  
    -   Sur le **Application** modifiez **framework cible** à **4.6.1**.  
  
    -   Sur le **Debug** sous l’onglet du **Démarrer le programme externe** tapez **\< chemin d’installation de Visual Studio \> \\Common7\\IDE\\devenv.exe.**.  
  
         Dans le **arguments de ligne de commande** tapez \/**rootsuffix Exp**.  
  
7.  Mettre à jour les références suivantes :  
  
    -   Supprimez la référence à Microsoft.VisualStudio.Shell.9.0.dll, puis ajoutez les références à Microsoft.VisualStudio.Shell.14.0.dll et Microsoft.VisualStudio.Shell.Immutable.11.0.dll.  
  
    -   Supprimez la référence à Microsoft.VisualStudio.Package.LanguageService.9.0.dll, puis ajoutez une référence à Microsoft.VisualStudio.Package.LanguageService.14.0.dll.  
  
    -   Ajoutez une référence à Microsoft.VisualStudio.Shell.Interop.10.0.dll.  
  
8.  Ouvrez le fichier VsPkg.cs et modifiez la valeur de la `DefaultRegistryRoot` attribut  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. L’exemple d’origine n’enregistre pas son service de langage, vous devez ajouter l’attribut suivant à VsPkg.cs.  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. Vous devez ajouter un fichier source.extension.vsixmanifest.  
  
    -   Copiez ce fichier à partir d’une extension existante de votre projet. \(Pour obtenir ce fichier consiste à créer un projet VSIX \(sous **fichier**, cliquez sur **nouveau**, puis cliquez sur **projet**. Cliquez sur sous Visual Basic ou c\# **extensibilité**, puis sélectionnez **projet VSIX**.\)  
  
    -   Ajoutez le fichier à votre projet.  
  
    -   Dans du fichier **propriétés**, définissez **Action de génération** à **aucun**.  
  
    -   Ouvrez le fichier avec le **éditeur de manifeste VSIX**.  
  
    -   Modifier les champs suivants :  
  
    -   **ID**: RegExLangServ  
  
    -   **Nom de produit**: RegExLangServ  
  
    -   **Description**: un service de langage d’expression régulière.  
  
    -   Sous **actifs**, cliquez sur **nouveau**, sélectionnez le **Type** à **Microsoft.VisualStudio.VsPackage**, définissez le **Source** à **un projet dans la solution actuelle**, puis définissez la **projet** à **RegExLangServ**.  
  
    -   Enregistrez et fermez le fichier.  
  
11. Générez la solution. Les fichiers créés sont déployées sur **%USERPROFILE%\\AppData\\Local\\Microsoft\\VisualStudio\\14.0Exp\\Extensions\\MSIT\\ RegExLangServ\\**.  
  
12. Démarrez le débogage. Une deuxième instance de Visual Studio ouvert.  
  
## Voir aussi  
 [Extensibilité du Service de langage ancien](../../extensibility/internals/legacy-language-service-extensibility.md)